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