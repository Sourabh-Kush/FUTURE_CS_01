# 🔐 Vulnerability Assessment Report — OWASP Juice Shop
### Future Interns | Cyber Security Track | Task 1

---

## 📌 Overview

This project is a comprehensive **Vulnerability Assessment** performed on the **OWASP Juice Shop** — an intentionally vulnerable web application used for security testing and education.

The assessment was conducted as part of the **Future Interns Cyber Security Internship (Task 1)** to identify, classify, and document web application vulnerabilities using industry-standard tools.

---

## 🎯 Objective

- Identify common web vulnerabilities in a live web application
- Classify risks as **Low / Medium / High**
- Explain issues in simple, business-friendly language
- Provide clear remediation steps for each finding

---

## 🌐 Target

| Field | Details |
|---|---|
| **Application** | OWASP Juice Shop |
| **URL** | http://juice-shop.herokuapp.com |
| **IP Address** | 54.220.192.176 |
| **Hosting** | Amazon AWS (EU-West-1) |
| **Assessment Date** | June 2, 2026 |
| **Assessment Type** | Passive + Active Vulnerability Scan |

---

## 🛠️ Tools Used

| Tool | Version | Purpose |
|---|---|---|
| **Nmap** | 7.99 | Port scanning & service detection |
| **OWASP ZAP** | 2.17.0 | Web application vulnerability scanning |
| **Browser DevTools** | Chrome | Security headers & cookie analysis |
| **Canva** | — | Professional report design |

---

## 📊 Summary of Findings

| Risk Level | Count |
|---|---|
| 🔴 High | 2 |
| 🟠 Medium | 4 |
| 🟡 Low | 4 |
| 🔵 Informational | 3 |
| **Total** | **13** |

---

## 🔍 Vulnerabilities Found

| # | Vulnerability | Risk | Tool | CWE |
|---|---|---|---|---|
| 1 | PII Disclosure (Credit Card Data Exposed) | 🔴 High | ZAP | CWE-359 |
| 2 | SQL Injection - SQLite | 🔴 High | ZAP | CWE-89 |
| 3 | Content Security Policy (CSP) Header Not Set | 🟠 Medium | ZAP + DevTools | CWE-693 |
| 4 | Cross-Domain Misconfiguration (CORS) | 🟠 Medium | ZAP + DevTools | CWE-264 |
| 5 | Missing Anti-clickjacking Header | 🟠 Medium | ZAP | CWE-1021 |
| 6 | Session ID in URL Rewrite | 🟠 Medium | ZAP | CWE-598 |
| 7 | Application Error Disclosure | 🟡 Low | ZAP | CWE-550 |
| 8 | Private IP Disclosure | 🟡 Low | ZAP | CWE-497 |
| 9 | Timestamp Disclosure - Unix | 🟡 Low | ZAP | CWE-497 |
| 10 | X-Content-Type-Options Header Missing | 🟡 Low | ZAP + DevTools | CWE-693 |
| 11 | Insecure Cookies (No HttpOnly/Secure/SameSite) | 🟠 Medium | DevTools | CWE-614 |
| 12 | Re-examine Cache-control Directives | 🔵 Info | ZAP | CWE-525 |
| 13 | Retrieved from Cache | 🔵 Info | ZAP | CWE-525 |

---

## 🗂️ Repository Structure

```
FUTURE_CS_01/
│
├── README.md                            ← Project overview (this file)
│
├── nmap_juiceshop.txt                   ← Nmap scan on Juice Shop
├── nmap_scan.txt                        ← Nmap scan on testphp.vulnweb.com
├── ZAP-Juice-Shop-Report.pdf            ← Full ZAP automated scan report
├── Vulnerability-Assessment-Report.pdf  ← Final professional Canva report
│
└── screenshots/
    │
    ├── Nmap/
    │   ├── nmap_result_1.png            ← Nmap scan output (part 1)
    │   ├── nmap_result_2.png            ← Nmap scan output (part 2)
    │   ├── nmap_result_3.png            ← Nmap scan output (part 3)
    │   └── nmap_result_4.png            ← Nmap scan output (part 4)
    │
    ├── ZAP/
    │   ├── zap_start.png                ← ZAP scan started
    │   ├── zap_100%.png                 ← ZAP scan 100% complete
    │   ├── zap_alerts.png               ← ZAP alerts overview
    │   ├── zap_scan_complete.png        ← ZAP scan completion screen
    │   └── Alerts/
    │       ├── Alert 1 - PII Disclosure (2).png
    │       ├── Alert 2 - SQL Injection - SQLite.png
    │       ├── Alert 3 - Content Security Policy (CSP) Header Not Set (Systemic).png
    │       ├── Alert 4 - Cross-Domain Misconfiguration (Systemic).png
    │       ├── Alert 5 - Missing Anti-clickjacking Header (2).png
    │       ├── Alert 6 - Session ID in URL Rewrite (Systemic).png
    │       ├── Alert 7 - Application Error Disclosure.png
    │       ├── Alert 8 - Private IP Disclosure.png
    │       ├── Alert 9 - Timestamp Disclosure - Unix (Systemic).png
    │       ├── Alert 10 - X-Content-Type-Options Header Missing (4).png
    │       ├── Alert 11 - Modern Web Application (Systemic).png
    │       ├── Alert 12 - Re-examine Cache-control Directives (2).png
    │       └── Alert 13 - Retrieved from Cache (2).png
    │
    └── devtools/
        ├── devtools_cookies.png         ← Insecure cookies (no HttpOnly/Secure)
        ├── devtools_headers.png         ← Response headers overview
        ├── devtools_headers_1.png       ← Headers detail (part 1)
        ├── devtools_headers_2.png       ← Headers detail (part 2)
        └── devtools_headers_3.png       ← Headers detail (part 3)
```

---

## 🔑 Nmap Findings Summary

| Port | State | Service | Finding |
|---|---|---|---|
| 80/tcp | Open | HTTP | Heroku Router — OWASP Juice Shop |
| 443/tcp | Open | HTTPS | SSL/TLS — Valid until 2027-01-29 |
| 2000/tcp | Open | cisco-sccp? | Unrecognized service |

**Additional Nmap Findings:**
- `/ftp` directory disallowed in robots.txt but potentially accessible
- CORS enabled for all methods: `HEAD GET POST PUT DELETE PATCH`
- Server technology disclosed: `Heroku / heroku-router`
- Hosted on AWS EC2 EU-West-1

---

## 🍪 Cookie Security Issues (DevTools)

| Cookie | HttpOnly | Secure | SameSite | Risk |
|---|---|---|---|---|
| `language` | ❌ Missing | ❌ Missing | ❌ Missing | 🟠 Medium |
| `welcomebanner_status` | ❌ Missing | ❌ Missing | ❌ Missing | 🟠 Medium |

---

## 🛡️ Top Remediation Steps

| Priority | Vulnerability | Fix |
|---|---|---|
| 1 | SQL Injection | Use parameterized queries / prepared statements |
| 2 | PII Disclosure | Audit API responses, never expose sensitive data |
| 3 | CSP Header Missing | Add `Content-Security-Policy` header to all responses |
| 4 | CORS Misconfiguration | Restrict `Access-Control-Allow-Origin` to trusted domains |
| 5 | Insecure Cookies | Add `HttpOnly`, `Secure`, and `SameSite` flags |
| 6 | FTP Directory Exposed | Restrict or remove public `/ftp` directory access |

---

## 📚 Skills Gained

- Vulnerability analysis & risk classification
- Web application security testing (OWASP Top 10)
- Network scanning & enumeration with Nmap
- Automated web scanning with OWASP ZAP
- Security headers & cookie analysis with DevTools
- Professional security reporting & documentation

---

## 👤 Author

**Sourabh**
Cyber Security Intern — Future Interns
GitHub: https://github.com/Sourabh-Kush
LinkedIn: https://www.linkedin.com/in/sourabh-kushwaha-41221b2a4/

---

*⚠️ Disclaimer: This assessment was conducted on an intentionally vulnerable application (OWASP Juice Shop) for educational purposes only. All testing was performed legally and ethically.*
