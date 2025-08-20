# 🔎Information gathering business

## 1. Mapear colaboradores

- **LinkedIn**: identificar funcionários e funções estratégicas (TI, Dev, Security, Diretoria, Financeiro).  
- **Outras redes sociais**: analisar interesses e comportamentos que podem indicar exposição de informações.  
- **Ferramentas auxiliares**:
  - Hunter.io (descobrir e-mails e padrões de nomenclatura)  
  - Clearbit, RocketReach (enriquecimento de perfis)
---

## 2. Mapear tecnologias e infraestrutura

- **Vagas de emprego**: indicam tecnologias, frameworks e ferramentas utilizadas.  
- **Projetos públicos**: GitHub, GitLab, Bitbucket.  
- **Blogs ou postagens técnicas**: informações sobre stacks, arquiteturas e incidentes passados.  

---

## 3. Google Dorking

```bash
https://www.exploit-db.com/google-hacking-database
ex:
https://www.google.com/search?q=site:linkedin.com+$target
https://google.com/search?q=site:pastebin.com+$target
https://google.com/search?q=site:trello.com
```
## 4. Domain Search → listar todos os e-mails vinculados a um domínio alvo
```bash
https://hunter.io/
```
```bash
Alternativas: Snov.io, VoilaNorbert, Clearbit
```
## 5. theHarvester - Coleta de informações públicas
```bash
theHarvester -d site.com -b all
nano /etc/theHarvester/apikeys.yaml
```

## 6. Domínios similares / typosquatting
```bash
urlcrazy -r empresa.com  # Reconhecimento Passivo
urlcrazy empresa.com  # Reconhecimento Ativo (resolve DNS)
```

## 7. Arquivos antigos e histórico de sites
```bash
web.archive.org
```

## 8. Análise de metadados
```bash
exiftool arq.ext
```

## 9. Vazamentos de dados públicos
```bash
https://haveibeenpwned.com/
dehashed.com
```

## 10. Vazamentos de dados tor
```bash
https://github.com/decoxviii/karma
ou
pwndb2am4tzkvold.onin
```
