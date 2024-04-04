# Server-side Vulnerabilities

Server-side vulnerabilities refer to security weaknesses that exist in the backend components of web applications, such as servers, databases, and application logic. Unlike client-side vulnerabilities, which often involve manipulating user inputs or interactions, server-side vulnerabilities typically require an understanding of the underlying server operations and application architecture.

Common types of server-side vulnerabilities include SQL Injection, Authentication flaws, Path Traversal, Command Injection, and Business Logic Vulnerabilities, among others. These vulnerabilities can expose sensitive data, compromise user privacy, and even lead to complete system compromise if exploited.

Understanding server-side vulnerabilities is crucial for anyone involved in web application security, as they are often the target of malicious attackers aiming to gain unauthorized access, manipulate data, or execute arbitrary code on the server.

## Path Traversal

![directory-traversal](https://github.com/acibojbp/Burp-Suite-Academy/assets/164168280/fb5222be-50ca-4fc2-bc55-b7871c751fc3)

Path traversal, also referred to as directory traversal, vulnerabilities allow attackers to access and manipulate files on the server, potentially exposing sensitive information. If attackers can modify these files, they may alter application data or behavior, gaining complete control over the server.

[File path traversal, simple case](../server-side-topics/path-traversal/lab-01/lab-01.md)
