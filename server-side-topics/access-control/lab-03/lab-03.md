# User role controlled by request parameter

https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter

This lab has an admin panel at `/admin`, which identifies administrators using a forgeable cookie.
Solve the lab by accessing the admin panel and using it to delete the user `carlos`.
You can log in to your own account using the following credentials: `wiener:peter`

## Solution

Logging in using the provided credentials while observing the packets sent using Burp Suite.
We can see on the Request 
```
GET /my-account?id=wiener HTTP/2
Host: 0a930025035210bf80e7809100c900d4.web-security-academy.net
Cookie: Admin=false; session=yTt95FTlbWgODCvtm5PUp53nAwb6NWAq
```

Let's go to Inspect > Application and here we can see the Cookies requested. Lets change the value of `Admin=false` to `Admin=true` and refresh the page.

A new option would be available to us, the Admin panel. From here we can delete the user `carlos`
