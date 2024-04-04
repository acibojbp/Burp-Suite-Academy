# Server-side Vulnerabilities

Server-side vulnerabilities refer to security weaknesses that exist in the backend components of web applications, such as servers, databases, and application logic. Unlike client-side vulnerabilities, which often involve manipulating user inputs or interactions, server-side vulnerabilities typically require an understanding of the underlying server operations and application architecture.

Common types of server-side vulnerabilities include SQL Injection, Authentication flaws, Path Traversal, Command Injection, and Business Logic Vulnerabilities, among others. These vulnerabilities can expose sensitive data, compromise user privacy, and even lead to complete system compromise if exploited.

Understanding server-side vulnerabilities is crucial for anyone involved in web application security, as they are often the target of malicious attackers aiming to gain unauthorized access, manipulate data, or execute arbitrary code on the server.

## Path Traversal

![directory-traversal](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/fb5222be-50ca-4fc2-bc55-b7871c751fc3)

Path traversal, also referred to as directory traversal, vulnerabilities allow attackers to access and manipulate files on the server, potentially exposing sensitive information. If attackers can modify these files, they may alter application data or behavior, gaining complete control over the server.

[File path traversal, simple case](../server-side-topics/path-traversal/lab-01/lab-01.md)

## Access Control

![access-control](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/14037cd2-1b10-48fc-95b8-06ad907574a3)

Access controls are implemented to restrict users from accessing data or features they are not authorized to use. Broken access controls pose significant security risks and are considered critical vulnerabilities. Additionally, they can expand the attack surface, potentially exposing other vulnerabilities.

Unprotected admin functionality
Unprotected admin functionality with unpredictable URL
User role controlled by request parameter
User ID controlled by request parameter, with unpredictable user IDs
User ID controlled by request parameter with password disclosure

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


