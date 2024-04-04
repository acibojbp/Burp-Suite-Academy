# Unprotected admin functionality

https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality

This lab has an unprotected admin panel.
Solve the lab by deleting the user `carlos`.

## Solution

We can solve this by going inside the `robots.txt` file. Here we can see :
```
User-agent: *
Disallow: /administrator-panel
```

We can simply go to this page and from here complete our objective, to delete the user `carlos`

```
https://0a8600bd0387a45b8380aa630059007f.web-security-academy.net/administrator-panel
```


