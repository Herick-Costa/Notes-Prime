
## SPF Sender Policy Framework
### Visa identificar quais servidores estão autorizados a enviar emails em nome do seu nominio
```bash
host -t txt dominio.com
```
### ?all --> susceptible*
### ~all --> susceptible*
### -all --> not susceptible
### Se não retornar nada está sem configuração

## exemplo de e-mails falsos

```bash
emkei.cz
```

## Subdomain takeover
### ex: dev.site.com --cname--> businesscorp.s3.amazon.com (desativado)
### Se o DNS aponta para o serviço que está desativado o nome do bucket pode estar disponivel
### como detectar
```bash
host -t cname dev.site.com
```

### script exemplo
```bash
#!/bin/bash
for x in $(cat sub_domains_descobertos.txt);do
host -t cname $x | grep "alias for"
done
```

## Outra ferramentas DNS

### 
```bash
dig -t ns site.com +short   #-t igual a host
dig -t axfr site.com @servidor.site.com  #transferencia de zona

```

### dnsenum
```bash
dnsenum --enum site.com

```

### dnsrecon
```bash
dnsrecon -d site.com

```

### fierce
```bash
fierce -dns site.com   #tranferencia de zona e brute force

```
### /usr/share/dns/ -> ferramentas e wordlists

## Mirror Website
### Linha de comando
```bash
wget -m -e robots=off site.com

```
```bash
httrack http://site.com -O mirror-site
httrack http://site.com -O mirror-site -v    #baixa e mantem estrutura
httrack "http://site.com" "+*.site.com/*" -O mirror-site      #inclui subdominios

```
### GUI
```bash
webhttrack

```

## Requisições HTTP
```bash
nc -v site.com
GET / HTTP/1.1
OPTIONS / HTTP/1.1

```
## Identificação de tecnologias
### whatweb
```bash
whatweb site.com
whatweb -a site.com

```
### wappalyzer - extenção de navegador

### BuiltWith
```bash
https://builtwith.com/

```
## NMAP
```bash
nmap -sn 172.30.0.0/24
```
```bash
nmap -sS -Pn site.com --reason   #reason traz o motivo das marcações
```
```bash
nmap -sT -Pn site.com
```
```bash
nmap -sU -Pn site.com
```
```bash
-sC (script default vulns)| -V (script)| -O (sistema operacional)| --top-ports=100 | -T 2 (Velocidade) 
```
```bash
nmap -v -sS -Pn -g 53 172.16.1.5
```
```bash
nmap -v -D RND:20 -sS --open 172.16.1.5
```
```bash
nmap -v -sV -p 443 --script=smb* 172.16.1.5
```
```bash
nmap -p 443 --script http-methods --script-args http-methods.url-path='/index.php'
```
```bash
ls /usr/share/nmap/scripts
```

## Scapy - ferramenta de manipulação de pacotes

## wpscan
```bash
wpscan --url http://172.23.1.50:8080/blog
```

## Nikto
```bash
nikto -h https://172.20.20.20 -p 8080
```

## Burp Suite



https://github.com/secdec/attack-surface-detector-cli/releases dar atenção e ver onde encaixa e como usa
tenho que aprender sobre o ZAP tbm
