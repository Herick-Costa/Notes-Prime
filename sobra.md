
## 📌FreeRDP
```bash
xfreerdp /u:<user> /d:<domain> /p:<password> /v:<ip> /sec:rdp /cert:ignore /auto-reconnect /drive:shared,/caminho/da/pasta/local
```

# 🛠️ Recursos Adicionais
- **Nmap Scripts**: `/usr/share/nmap/scripts`
- **msfvenom Cheatsheet**:`https://blog.ironlinux.com.br/msfvenom-cheatsheet/`
- **Metasploit Payloads**: `msfvenom -l payloads | grep "windows"`
- **FreeRDP**: `xfreerdp /u:<user> /d:<domain> /p:<password> /v:<ip> /sec:rdp /cert:ignore /auto-reconnect`
- hydra -L usuarios.txt -P senhas.txt IP_DO_ALVO http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&testcookie=1:S=Location" -V
- evil-winrm -i 10.10.10.10 -u username -p password  (porta windows 5985 / 5986)
