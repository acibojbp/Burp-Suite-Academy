# Unprotected admin functionality with unpredictable URL

https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality-with-unpredictable-url

This lab has an unprotected admin panel. It's located at an unpredictable location, but the location is disclosed somewhere in the application.

Solve the lab by accessing the admin panel, and using it to delete the user `carlos`.

## Solution

Using Burp Suite, we can see that the source code contains this script :

```javascript
<script>
var isAdmin = false;
if (isAdmin) {
   var topLinksTag = document.getElementsByClassName("top-links")[0];
   var adminPanelTag = document.createElement('a');
   adminPanelTag.setAttribute('href', '/admin-pyh99h');
   adminPanelTag.innerText = 'Admin panel';
   topLinksTag.append(adminPanelTag);
   var pTag = document.createElement('p');
   pTag.innerText = '|';
   topLinksTag.appendChild(pTag);
}
</script>
```

From this, we can deduce that the address for the admin panel is `/admin/pyh99h`
```
https://0a1500d1037ccc1c82b4842700fd00d9.web-security-academy.net/admin-pyh99h
```

And from here we can access the admin panel and delete the user `carlos` and we have solved the lab.
