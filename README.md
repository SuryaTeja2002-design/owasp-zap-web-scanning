# 🔍 Web App Scanning with OWASP ZAP

> **Cybersecurity Portfolio Project #5**  
> Tools: OWASP ZAP 2.17.0 | Target: DVWA | Platform: Kali Linux | Date: April 2026

---

## 📋 Project Overview

This project demonstrates web application vulnerability scanning using **OWASP ZAP (Zed Attack Proxy)**, one of the most widely used open-source web app security tools in the world. The target was **DVWA (Damn Vulnerable Web Application)** — a deliberately vulnerable app designed for security training.

All scanning was performed in a controlled, isolated lab environment against systems I own and control.

---

## 🧪 Lab Environment

| Component | Details |
|-----------|---------|
| OS | Kali Linux (VirtualBox VM) |
| OWASP ZAP Version | 2.17.0 |
| Target App | DVWA (Damn Vulnerable Web Application) |
| Target URL | http://127.x.x.x/dvwa |
| Web Server | Apache 2.4.65 |
| Database | MariaDB |
| Network | NAT (VirtualBox isolated) |

---

## 🛠️ Setup & Configuration

### Services Started
```bash
sudo service apache2 start
sudo service mariadb start
```

### DVWA Installation
```bash
sudo apt install dvwa -y
sudo cp -r /usr/share/dvwa /var/www/html/dvwa
```

### Database Setup
```bash
sudo mysql -u root -e "CREATE DATABASE dvwa; CREATE USER 'dvwa'@'localhost' IDENTIFIED BY ''; GRANT ALL ON dvwa.* TO 'dvwa'@'localhost'; FLUSH PRIVILEGES;"
```

### Launch ZAP
```bash
zaproxy
```

---

## 🚀 Scan Performed

### Automated Scan
Using ZAP's built-in **Automated Scan** feature:
- URL targeted: `http://127.x.x.x/dvwa`
- Traditional Spider: ✅ Enabled
- Ajax Spider: ✅ Enabled
- Active Scan: ✅ Running

The automated scan performs two phases:
1. **Spider** — crawls the entire web app, mapping all pages and endpoints
2. **Active Scan** — fires attack payloads at every endpoint testing for vulnerabilities

---

## 📊 DVWA Vulnerability Modules Targeted

| Module | Vulnerability Type | OWASP Category |
|--------|-------------------|----------------|
| Brute Force | Weak authentication | A07: Auth Failures |
| Command Injection | OS command injection | A03: Injection |
| SQL Injection | Database injection | A03: Injection |
| SQL Injection (Blind) | Blind SQLi | A03: Injection |
| XSS (Reflected) | Cross-site scripting | A03: Injection |
| XSS (Stored) | Persistent XSS | A03: Injection |
| XSS (DOM) | DOM-based XSS | A03: Injection |
| CSRF | Cross-site request forgery | A01: Broken Access |
| File Inclusion | Path traversal | A01: Broken Access |
| File Upload | Unrestricted upload | A04: Insecure Design |

---

## 🔐 Security Analysis

**Why DVWA is used for training:**
DVWA intentionally contains all OWASP Top 10 vulnerability classes, making it the ideal target for learning how scanners like ZAP detect real-world issues without risking unauthorized access to live systems.

**What ZAP tests for:**
- SQL Injection — can an attacker extract database contents?
- XSS — can malicious scripts be injected into pages?
- CSRF — can attackers trick users into performing actions?
- Broken authentication — are sessions and credentials weak?
- Security misconfigurations — are server headers exposing sensitive info?

---

## 🖼️ Evidence — Live Scan Screenshots

The following screenshots were captured during the live assessment on Kali Linux.

**DVWA Login Page — Target confirmed live:**

<img width="1351" height="856" alt="image" src="https://github.com/user-attachments/assets/82e60482-7c44-44fb-b00a-f2c0257b54c8" />

**DVWA Dashboard — Vulnerability modules visible:**

<img width="1568" height="507" alt="image" src="https://github.com/user-attachments/assets/3fc22131-6d17-4351-93c9-fa1851bddbe5" />

**OWASP ZAP Active Scan — 36% progress, actively scanning:**

<img width="1372" height="875" alt="image" src="https://github.com/user-attachments/assets/1791d483-f56c-4285-b67e-4ebb308d8499" />

---

## 📁 Repository Structure

```
owasp-zap-web-scanning/
├── README.md                      ← This file
├── OWASP_ZAP_Portfolio_Report.docx ← Full written report
```

---

## 🛠️ ZAP Features Used

| Feature | Purpose |
|---------|---------|
| Automated Scan | One-click spider + active scan |
| Traditional Spider | Crawls all links and forms |
| Ajax Spider | Crawls JavaScript-heavy pages |
| Active Scanner | Fires attack payloads at endpoints |
| Alerts Panel | Lists all vulnerabilities found with severity |
| Report Generator | Exports findings to HTML/PDF/JSON |

---

## ⚠️ Ethical Notice

All scanning in this project was performed exclusively against **DVWA**, a deliberately vulnerable application running on systems I own and control in a private lab environment. **Scanning web applications without explicit written authorization is illegal.** Always obtain permission before conducting any security assessment.

---

## 🔗 Related Projects

- [ ] Project 1 — Active Directory Setup & User Management
- [ ] Project 2 — Cloud Security Risk Assessment (GRC)
- [ ] Project 3 — Log File Analysis / SIEM Virtualization
- [x] Project 4 — Network & Host Scanning with Nmap ✅
- [x] Project 5 — Web App Scanning with OWASP ZAP ✅
