## 🔄 Tunelamento de porta via SSH
Encerramos a conexão SSH e realizamos novamente tunelando a porta 10000 com o comando:
```bash
ssh -L (qq port)10000:localhost:10000(service port) agent47@10.10.54.4
```
