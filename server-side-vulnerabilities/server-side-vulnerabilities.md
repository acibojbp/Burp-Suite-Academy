# Server-side Vulnerabilities

Server-side vulnerabilities refer to security weaknesses that exist in the backend components of web applications, such as servers, databases, and application logic. Unlike client-side vulnerabilities, which often involve manipulating user inputs or interactions, server-side vulnerabilities typically require an understanding of the underlying server operations and application architecture.

Common types of server-side vulnerabilities include SQL Injection, Authentication flaws, Path Traversal, Command Injection, and Business Logic Vulnerabilities, among others. These vulnerabilities can expose sensitive data, compromise user privacy, and even lead to complete system compromise if exploited.

Understanding server-side vulnerabilities is crucial for anyone involved in web application security, as they are often the target of malicious attackers aiming to gain unauthorized access, manipulate data, or execute arbitrary code on the server.

## Contents
[Path Traversal](#path-traversal)

[Access Control](#access-control)

[Authentication](#authentication)

[Server-side Request Forgery](#server-side-request-forgery)

[File Upload Vulnerabilities](#file-upload-vulnerabilities)

[OS Command Injection](#os-command-injection)

[SQL Injection](#sql-injection)

## Path Traversal

![directory-traversal](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/fb5222be-50ca-4fc2-bc55-b7871c751fc3)

Path traversal, also referred to as directory traversal, vulnerabilities allow attackers to access and manipulate files on the server, potentially exposing sensitive information. If attackers can modify these files, they may alter application data or behavior, gaining complete control over the server.

[File path traversal, simple case](../server-side-topics/path-traversal/lab-01/lab-01.md)

## Access Control

![access-control](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/14037cd2-1b10-48fc-95b8-06ad907574a3)

Access controls are implemented to restrict users from accessing data or features they are not authorized to use. Broken access controls pose significant security risks and are considered critical vulnerabilities. Additionally, they can expand the attack surface, potentially exposing other vulnerabilities.

[Unprotected admin functionality](../server-side-topics/access-control/lab-01/lab-01.md)

[Unprotected admin functionality with unpredictable URL](../server-side-topics/access-control/lab-02/lab-02.md)

[User role controlled by request parameter](../server-side-topics/access-control/lab-03/lab-03.md)

[User ID controlled by request parameter, with unpredictable user IDs](../server-side-topics/access-control/lab-08/lab-08.md)

[User ID controlled by request parameter with password disclosure](../server-side-topics/access-control/lab-10/lab-10.md)

## Authentication

![password-reset-poisoning](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/248c5a18-8365-43f8-acac-354c1671bcf3)

Authentication verifies the identity of a user to ensure they are who they claim to be. For instance, a login system requiring a username and password is a common authentication method. However, flawed authentication systems can enable attackers to guess legitimate credentials by automating numerous login attempts using specialized tools such as Burp Intruder.

Username enumeration via different responses

2FA simple bypass

## Server-side Request Forgery

![server-side request forgery](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/a5bb4ed5-ccf5-49a9-b9fc-f6817ab3a983)

SSRF vulnerabilities allow attackers to initiate harmful server-to-server requests to unintended URLs. Since the server making the request often has a trusted relationship with other network systems, attackers can potentially exploit this to access data, features, and services that should not be accessible to external users.

Basic SSRF against the local server

Basic SSRF against another back-end system

## File Upload Vulnerabilities

![file-upload-vulnerabilities](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/b8e18357-af31-4752-bd9b-2c36578de206)

Any feature that allows users to upload files to the server's filesystem poses inherent risks. Neglecting to implement appropriate restrictions on the types of files users can upload may allow attackers to execute arbitrary system commands, granting them complete control over the server.

Remote code execution via web shell upload

Web shell upload via Content-Type restriction bypass

## OS Command Injection

![os-command-injection](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/57531897-bd8b-4d93-b71f-df6cb93014cc)

Command injection vulnerabilities allow attackers to run arbitrary operating system (OS) commands on the server, granting them complete control over the server and compromising both the application and its data.

OS command injection, simple case

## SQL Injection

![sql-injection](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/4f87cd27-15b4-4c7c-b94f-3ed269e30997)

SQL injection is a well-known vulnerability that has been the cause of numerous high-profile data breaches. It allows attackers to manipulate the queries sent by the application to its database, potentially accessing sensitive data from any table within the database.

SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

SQL injection vulnerability allowing login bypass
