# google-dorks-mindtree
Visual recon dashboard for Google Dorking (Pentesters &amp; Bug Bounty)


# 🔍 Google Dorks — Mind Tree Edition v5.0
### OSINT Recon Framework | 102 Dorks | 10 Categories | Bug Bounty Ready

![Version](https://img.shields.io/badge/version-5.0.0-brightgreen)
![Dorks](https://img.shields.io/badge/dorks-102-blue)
![Categories](https://img.shields.io/badge/categories-10-orange)
![High Value](https://img.shields.io/badge/high--value-73-red)
![Status](https://img.shields.io/badge/status-active-success)
![License](https://img.shields.io/badge/license-Educational-yellow)

> **Author:** Binesh Madharapu — Cybersecurity Researcher | OSINT Specialist | Penetration Tester  
> **LinkedIn:** [linkedin.com/in/bineshmadharapu](https://linkedin.com/in/bineshmadharapu)  
> **Updated:** 2026

---

## 📌 What is This?

**Google Dorks — Mind Tree** is a comprehensive, visually organized reference tool for Google Dorking (also known as Google Hacking). It provides 102 carefully crafted search queries organized into 10 attack surface categories, designed for:

- 🔴 **Penetration Testers** — passive recon before an engagement
- 🟡 **Bug Bounty Hunters** — finding exposed assets on in-scope targets
- 🔵 **OSINT Researchers** — gathering intelligence from public sources
- 🟢 **Security Auditors** — identifying misconfigurations in your own infrastructure

---

## 🧠 What is Google Dorking?

Google Dorking uses **advanced search operators** to surface information that is publicly indexed but not easily discoverable through normal searches. Common operators used:

| Operator | Description | Example |
|---|---|---|
| `site:` | Restrict results to a domain | `site:target.com` |
| `inurl:` | Search within URLs | `inurl:admin` |
| `intitle:` | Search within page titles | `intitle:"index of"` |
| `intext:` | Search within page content | `intext:"api_key"` |
| `filetype:` | Filter by file extension | `filetype:env` |
| `ext:` | Filter by file extension | `ext:sql` |
| `OR` | Match either term | `ext:bak OR ext:old` |

---

## 📂 Categories

### 1. 📁 File & Directory Exposure (10 dorks)
Finds open directories, exposed configuration files, backups, and sensitive file types.

```
intitle:"index of" site:target.com
site:target.com ext:sql
site:target.com ext:env
site:target.com ext:log
site:target.com ext:bak OR ext:old OR ext:backup
site:target.com ext:zip OR ext:tar OR ext:gz "backup"
site:target.com filetype:xls OR filetype:xlsx
intitle:"index of" ".git" site:target.com
site:target.com inurl:.DS_Store
intitle:"index of" "parent directory" site:target.com
```

---

### 2. 🔑 Credentials & Secrets (11 dorks)
Discovers exposed API keys, passwords, tokens, and cloud credentials.

```
site:target.com intext:"password" filetype:log
site:target.com intext:"api_key" OR intext:"apikey"
site:target.com filetype:js intext:"apiKey"
site:target.com intext:"firebaseConfig"
site:target.com intext:"secret_key" OR intext:"SECRET_KEY"
site:target.com intext:"db_password" OR intext:"DB_PASS"
site:target.com ext:env intext:"AWS_SECRET"
site:target.com intext:"Authorization: Bearer"
site:target.com intext:"-----BEGIN RSA PRIVATE KEY-----"
site:pastebin.com "target.com" password
site:github.com "target.com" password OR secret
```

---

### 3. 🔒 Login & Admin Panels (11 dorks)
Locates admin portals, login pages, and management interfaces.

```
site:target.com inurl:admin
site:target.com inurl:login
site:target.com intitle:"admin panel" OR intitle:"admin login"
site:target.com inurl:wp-admin
site:target.com inurl:phpmyadmin
site:target.com inurl:cpanel OR inurl:plesk
site:target.com inurl:/admin/login.php
site:target.com intitle:"Kibana" inurl:5601
site:target.com intitle:"Grafana" inurl:3000
site:target.com inurl:/console intitle:"Tomcat"
site:target.com intitle:"Jenkins" inurl:/job
```

---

### 4. ⚡ Vulnerable Parameters (11 dorks)
Identifies potentially vulnerable URL parameters for SQLi, LFI, RFI, and command injection.

```
site:target.com inurl:id= ext:php
site:target.com inurl:"?page=" OR inurl:"?file="
site:target.com inurl:"redirect=" OR inurl:"url="
site:target.com inurl:"include=" OR inurl:"require="
site:target.com inurl:"cmd=" OR inurl:"exec="
site:target.com inurl:upload ext:php
site:target.com inurl:download ext:php inurl:file=
site:target.com inurl:swagger.json
site:target.com inurl:"/_next/"
site:target.com inurl:graphql
site:target.com inurl:/api/v1 OR inurl:/api/v2
```

---

### 5. 🔍 Info Disclosure (11 dorks)
Finds error messages, stack traces, and technology fingerprinting opportunities.

```
site:target.com intext:"sql syntax near" OR intext:"mysql_fetch"
site:target.com intext:"Fatal error" "on line"
site:target.com intext:"Warning: mysql" OR intext:"mysqli"
site:target.com intitle:"phpinfo()"
site:target.com "Apache/2" intitle:"Test Page"
site:target.com intitle:"error" intext:"stack trace"
site:target.com filetype:xml inurl:sitemap
site:target.com inurl:/robots.txt
site:target.com inurl:/.well-known
site:target.com intext:"X-Powered-By"
site:target.com inurl:swagger OR inurl:api-docs
```

---

### 6. 🌐 Network & Infrastructure (10 dorks)
Reveals exposed services, non-standard ports, and infrastructure components.

```
site:target.com ":8080" OR ":8443" OR ":8888"
site:target.com intitle:"VPN" OR intitle:"Remote Access"
site:target.com inurl:443 intitle:"Citrix"
site:target.com intitle:"Webmin"
site:target.com intitle:"RouterOS" inurl:webfig
site:target.com inurl:/actuator/env
site:target.com inurl:/actuator/heapdump
site:target.com inurl:/_cat/indices
site:target.com intitle:"MongoDB" inurl:28017
site:target.com inurl:redis inurl:6379
```

---

### 7. ☁️ Cloud & Buckets (10 dorks)
Discovers exposed cloud storage, misconfigured buckets, and cloud credentials.

```
site:s3.amazonaws.com "target.com"
site:blob.core.windows.net "target.com"
site:storage.googleapis.com "target.com"
inurl:s3.amazonaws.com intext:"target.com"
site:target.com inurl:".s3.amazonaws.com"
site:target.com filetype:yaml intext:"aws_access_key"
site:target.com inurl:/.git/config
site:github.com org:target.com
site:gitlab.com "target.com"
site:target.com intext:"firebase" intext:"apiKey"
```

---

### 8. 📡 Subdomain Recon (5 dorks)
Enumerates subdomains including dev, staging, API, and VPN endpoints.

```
site:*.target.com -site:www.target.com
site:*.target.com inurl:dev OR inurl:test OR inurl:staging
site:*.target.com inurl:api
site:*.target.com inurl:vpn OR inurl:remote
site:*.target.com intitle:"login"
```

---

### 9. 👤 OSINT & Social (7 dorks)
Finds employee information, data leaks, and public mentions across social platforms.

```
site:linkedin.com "target.com"
site:linkedin.com "@target.com"
site:pastebin.com "target.com"
site:trello.com "target.com"
site:github.com "target.com"
site:jira.atlassian.net "target.com"
site:scribd.com "target.com"
```

---

### 10. 🧩 CMS & Frameworks (9 dorks)
Identifies CMS platforms, version information, and framework-specific vulnerabilities.

```
site:target.com inurl:wp-content
site:target.com inurl:wp-json/wp/v2
site:target.com inurl:wp-config.php
site:target.com inurl:readme.txt "WordPress"
site:target.com inurl:CHANGELOG.txt
site:target.com inurl:/administrator intitle:"Joomla"
site:target.com intitle:"Powered by Drupal"
site:target.com inurl:magento OR inurl:/admin/sales
site:target.com inurl:strapi OR inurl:/admin/auth
```

---

## 🚀 How to Use

### Basic Usage
1. Open [Google](https://google.com)
2. Copy any dork from the list
3. Replace `target.com` with the domain you're **authorized** to test
4. Paste and search

### Example
```
# Replace target.com with a real domain
site:example.com ext:env
```

### Pro Tips
- 🔄 **Combine operators** for more precise results
- ⏱️ **Add `after:2023`** to filter recent results: `site:target.com ext:env after:2023`
- 🌍 Use **Google dorking with other OSINT tools** like Shodan, Recon-ng, or theHarvester
- 🚦 Be aware of **Google rate limiting** — too many queries may trigger a CAPTCHA
- 📋 Always **document your findings** during a pentest

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Frontend | Pure HTML5, CSS3, JavaScript |
| Font | Orbitron + Share Tech Mono (Google Fonts) |
| Theme | Custom cyberpunk dark theme |
| Architecture | Mind Tree v5 — single file, no dependencies |

---

## 📁 Project Structure

```
google-dorks-mind-tree/
│
├── index.html          # Main application (single-file)
├── README.md           # This file
└── screenshots/        # UI screenshots for documentation
    ├── header.png
    ├── file-exposure.png
    ├── credentials.png
    ├── admin-panels.png
    ├── vulnerable-params.png
    ├── info-disclosure.png
    ├── cloud-buckets.png
    └── footer.png
```

---

## ⚠️ Legal Notice

> **This tool is for authorized security research and educational purposes ONLY.**
>
> Unauthorized use against systems you do not own or have explicit written permission to test is **illegal** and may violate laws including the Computer Fraud and Abuse Act (CFAA), the Computer Misuse Act (CMA), and equivalent legislation in your country.
>
> **Always obtain written authorization before conducting security assessments.**
>
> The author assumes no liability for misuse of this tool.

---

## 🤝 Contributing

Contributions are welcome! If you have new dorks to add or improvements to suggest:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/new-dorks`
3. Add your dorks with proper comments and HIGH/LOW value tags
4. Submit a Pull Request with a description of what you added

---

## 📜 Changelog

### v5.0.0 (2026)
- Rebuilt as Mind Tree Edition with interactive UI
- Added 10 organized categories
- 102 total dorks (73 marked HIGH value)
- New categories: Cloud & Buckets, Subdomain Recon, OSINT & Social
- Screenshot mode added

### v4.x
- Initial public release
- Basic category structure

---

## 🏷️ Tags

`#GoogleDorking` `#OSINT` `#BugBounty` `#RedTeam` `#CyberSecurity` `#PenTesting` `#EthicalHacking` `#InfoSec` `#Recon` `#SecurityResearch`

---

## 📬 Contact

**Binesh Madharapu**  
Cybersecurity Researcher | OSINT Specialist | Penetration Tester  
🔗 [LinkedIn](https://linkedin.com/in/bineshmadharapu)

---

*⭐ If this project helped you, please give it a star!*
