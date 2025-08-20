# 🔎Information gathering Passivo

## Mapear colaboradores

- **LinkedIn**: identificar funcionários e funções estratégicas (TI, Dev, Security, Diretoria, Financeiro).  
- **Outras redes sociais**: analisar interesses e comportamentos que podem indicar exposição de informações.  
- **Ferramentas auxiliares**:
  - Hunter.io (descobrir e-mails e padrões de nomenclatura)  
  - Clearbit, RocketReach (enriquecimento de perfis)
---

## Mapear tecnologias e infraestrutura

- **Vagas de emprego**: indicam tecnologias, frameworks e ferramentas utilizadas.  
- **Projetos públicos**: GitHub, GitLab, Bitbucket.  
- **Blogs ou postagens técnicas**: informações sobre stacks, arquiteturas e incidentes passados.  

---

## Google Dorking

```bash
https://www.exploit-db.com/google-hacking-database
ex:
https://www.google.com/search?q=site:linkedin.com+$target
https://google.com/search?q=site:pastebin.com+$target
https://google.com/search?q=site:trello.com
```
## Domain Search → listar todos os e-mails vinculados a um domínio alvo
```bash
https://hunter.io/
```
```bash
Alternativas: Snov.io, VoilaNorbert, Clearbit
```
## theHarvester - Coleta de informações públicas
```bash
theHarvester -d site.com -b all
nano /etc/theHarvester/apikeys.yaml
```

## Domínios similares / typosquatting
```bash
urlcrazy -r empresa.com  # Reconhecimento Passivo
urlcrazy empresa.com  # Reconhecimento Ativo (resolve DNS)
```

## Arquivos antigos e histórico de sites
```bash
web.archive.org
```

## Análise de metadados
```bash
exiftool arq.ext
```

## Vazamentos de dados públicos
```bash
https://haveibeenpwned.com/
dehashed.com
```

## Vazamentos de dados tor
```bash
https://github.com/decoxviii/karma
ou
pwndb2am4tzkvold.onin
```

## IP Footprinting
```bash
whois 10.10.10.10 | grep -i "inetnum\|netname\|org"
```
### Consultas online
```bash
https://search.arin.net/rdap/?query=10.10.10.10
https://bgp.he.net/ip/10.10.10.10
https://bgpview.io/ip/10.10.10.10
https://ipinfo.io/10.10.10.10
https://www.virustotal.com/gui/ip-address/10.10.10.10

```

### ASN info
```bash
whois -h whois.cymru.com " -v 10.10.10.10"
```

### Subnet enumeration a partir do ASN
```bash
amass intel -asn <ASN>
```

---

## Shodan

- `os:Linux` → Sistema operacional  
- `port:1661` → Porta específica  
- `ip:10.10.10.12` → IP específico  
- `net:10.10.10.0/24` → Rede/CIDR  
- `country:BR` → País  
- `city:"São Paulo"` → Cidade  
- `geo:"-23.5505,-46.6333"` → Geolocalização  
- `org:"Google"` → Organização/ASN  
- `"Apache httpd"` → Termo exato  
- `domain:target.com` → Domínio associado  
- `API` → Usado quando logado com API Key para integrações (ex: theHarvester)

```bash
shodan init 'API Key'
shodan host 10.10.10.10
shodan search port:443 org:"Target Corp"
shodan search apache country:"BR"
shodan download resultado.json "domain:target.com"

```
---

## censys.io 

https://search.censys.io/

- `services.service_name:HTTP` → Tipo de serviço → **Ex:** `services.service_name:HTTP`  
- `services.tls.certificates.leaf_data.subject.common_name:target.com` → Domínio no certificado TLS → **Ex:** `services.tls.certificates.leaf_data.subject.common_name:example.com`  
- `ip:10.10.10.12` → IP específico → **Ex:** `ip:10.10.10.12`  
- `autonomous_system.asn:AS12345` → ASN → **Ex:** `autonomous_system.asn:AS15169`  
- `location.country:BR` → País → **Ex:** `location.country:BR`  
- `location.city:"São Paulo"` → Cidade → **Ex:** `location.city:"São Paulo"`  
- `services.tls.certificates.parsed.extensions.subject_alt_name.dns_names:"target.com"` → Subdomínios em SAN → **Ex:** `services.tls.certificates.parsed.extensions.subject_alt_name.dns_names:"www.example.com"`  
- `protocols:443/https` → Porta/Protocolo → **Ex:** `protocols:443/https`  
- `tags:"cloud"` → Tag do host → **Ex:** `tags:"aws"`  
- `API` → Usado quando logado com API Key para consultas via terminal ou scripts 

```bash
censys config # Configurar API Key
censys search "services.tls.certificates.leaf_data.subject.common_name: target.com"
censys search "autonomous_system.asn: AS12345"
censys search "services.service_name: HTTP AND ip:10.10.10.0/24" --output results.json

```
---
## Sublist3r - Enumeração de subdomínios via fontes públicas

```bash
sublist3r -d dominio.com 
```

## subfinder – Enumeração via APIs públicas
```bash
subfinder -d dominio.com -all -silent
```
## amass (modo passivo) – Coleta em fontes abertas

```bash
amass intel -d dominio.com -o subdominios.txt
```

## assetfinder – Subdomínios conhecidos 

```bash
assetfinder --subs-only dominio.com
```
## crobat – Consulta rápida de subdomínios

```bash
crobat -s dominio.com
```

## gau – Coleta URLs de fontes públicas (Wayback, Common Crawl, etc).

```bash
gau dominio.com
```

