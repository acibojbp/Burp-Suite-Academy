# User ID controlled by request parameter with password disclosure

https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure

This lab has user account page that contains the current user's existing password, prefilled in a masked input.
To solve the lab, retrieve the administrator's password, then use it to delete the user `carlos`.
You can log in to your own account using the following credentials: `wiener:peter`

## Solution

Logging in using the provided credentials, and observing Burp Suite
```
GET /my-account?id=wiener HTTP/2
Host: 0a5700f30408764e82485c70004a00ec.web-security-academy.net
Cookie: session=
```
We can see that the id is no longer a GUID and a simple username. The account page has an `Update Email` and `Update Password` forms. Checking the source code of the page, we are able to see that it provides the current value for the password.

```html
<form class="login-form" action="/my-account/change-password" method="POST"><br/>
	<label>Password</label>
		<input required type="hidden" name="csrf" value="ZMub9ViaKI2nY2u5VFVPmwACPXTl4Yt5">
		<input required type=password name=password value='peter'/>
		<button class='button' type='submit'> Update password 
		</button>
</form>
```

We need to know the password of the administrator, we need to send this packet to the Repeater and change the account from `wiener` to `administrator`.

```html
<input required type=password name=password value='3l5esvdnvf7vtw9qso40'/>
```
We can now see the value of the `administrator`'s password, we can log in as admin and delete the user `carlos` and the lab is sovled!
