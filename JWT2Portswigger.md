# Lab: JWT authentication bypass via flawed signature verification
---
In burpsuite we install "JSON Web Token" and "jwt editor"

This lab uses a JWT-based mechanism for handling sessions. The server is insecurely configured to accept unsigned JWTs.

Target: To solve the lab, modify your session token to gain access to the admin panel at /admin, then delete the user carlos.

https://0aa0008c03d4d53881183eea005600ed.web-security-academy.net/admin
