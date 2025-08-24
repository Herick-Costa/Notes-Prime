# Web Enumeration

## NMAP
```bash
nmap -sV 172.30.0.0/24
```
```bash
nmap -v -sV -p 443 --script=smb* 172.16.1.5
```

## Gobuster

```bash
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/big.txt
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/big.txt --retry --no--error -x php
```

## Feroxbuster

```bash

feroxbuster -u http://172.23.1.148/ -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-words.txt -A

feroxbuster -u http://172.23.1.148/ -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-large-files.txt -A

```

## Nikto
```bash
nikto -h https://172.20.20.20 -p 8080
```

## Burp Suite

## wpscan
```bash
wpscan --url http://172.23.1.50:8080/blog
- wpscan --url http://172.23.1.50:8080/blog --usernames leandro --passwords /usr/share/wordlists/rockyou.txt --enumerate u --force

```

## joomscan
```bash

```
