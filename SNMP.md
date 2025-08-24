# 🖧 SNMP

## 🔎 Reconhecimento 
```bash
nmap -sVU -p 161 -Pn 10.201.31.217
nmap -sU -p 161 --open 10.201.31.217
nmap -sU -p 161 --script=snmp-info 10.201.31.217
```

## 🔎 Testar as communitys
```bash
onesixtyone -c /usr/share/seclists/Discovery/SNMP/snmp-onesixtyone.txt 10.201.31.217
onesixtyone -c /usr/share/wordlists/metasploit/snmp_default_pass.txt 10.10.10.0/24
```

## 🔎 snmpwalk 
```bash
snmpwalk -c public -v1 10.10.10.10
snmpwalk -c public -v1 10.10.10.10 1.3.6.1.4.1.77.1.2.25   (nesse caso cod de users - sem eles testa varios)
snmpwalk -v2c -c public 10.10.10.10
```
## 🔎 snmptranslate (traduz)
```bash
snmptranslate 1.3.6.1.4.1.77.1.2.25
```

## 🔎 snmp-check 
```bash
snmp-check <IP-alvo> -c openview
snmp-check <IP-alvo> -c public
```

## 🔎 snmpset 
```bash
snmpset -c manager -v1 10.10.10.101 SNMP-MIB::sysContact.0 s "v"
```
