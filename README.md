# 🔐 Vulnerability Assessment Report — AltoroMutual

### Future Interns | Cyber Security Track | Task 1

---

## 📌 Overview

This project is a **read-only, passive Vulnerability Assessment** performed on **AltoroMutual** (demo.testfire.net) — a public demo banking application built for security testing and education.

The assessment was conducted as part of the **Future Interns Cyber Security Internship (Task 1)** to identify, classify, and document web application security weaknesses using industry-standard tools, strictly within a passive/non-intrusive scope.

---

## 🎯 Objective

- Identify common web security weaknesses in a live public web application
- Classify risks as **Low / Medium / Informational**
- Explain issues in simple, business-friendly language
- Provide clear remediation steps for each finding

---

## 🌐 Target

| Field | Details |
|---|---|
| **Application** | AltoroMutual |
| **URL** | http://demo.testfire.net |
| **IP Address** | 65.61.137.117 |
| **Hosting** | Amazon AWS (us-west-2) |
| **Assessment Date** | 19–22 September 2026 |
| **Assessment Type** | Passive / Read-Only Only (no exploitation, login bypass, brute force, or DoS) |

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Nmap** (Quick scan) | Port & service enumeration |
| **OWASP ZAP** (Passive Scan, Low threshold) | Identify issues by observing traffic — no active attacks |
| **Browser DevTools** | Response header and cookie configuration analysis |

---

## 📊 Summary of Findings

| Risk Level | Count |
|---|---|
| 🟠 Medium | 3 |
| 🟡 Low | 2 |
| 🔵 Informational | 1 |
| **Total** | **6** |

---

## 🔍 Vulnerabilities Found

| # | Finding | Risk | Tool |
|---|---|---|---|
| 1 | No HTTPS Enforcement | 🟠 Medium | Browser / DevTools |
| 2 | Missing Security Headers (CSP, X-Frame-Options, HSTS, X-Content-Type-Options) | 🟠 Medium | DevTools |
| 3 | Insecure Cookie Configuration (JSESSIONID missing `Secure` flag) | 🟠 Medium | DevTools |
| 4 | Server Version Disclosure (`Apache-Coyote/1.1`) | 🟡 Low | DevTools |
| 5 | Unnecessary Exposed Service on Port 8080 | 🟡 Low | Nmap |
| 6 | Session Management Response Identified | 🔵 Informational | OWASP ZAP |

---

## 🗂️ Repository Structure

```
FUTURE_CS_01/
│
├── README.md                            ← Project overview (this file)
├── Vulnerability_Assessment_Report.md   ← Full report content (source for Canva PDF)
├── nmap_scan.txt                        ← Raw Nmap scan output
│
└── evidence/
    │
    ├── nmap/
    │   └── 01_nmap_scan_output.png      ← Nmap scan result (Zenmap)
    │
    ├── zap/
    │   ├── 02_zap_passive_scan_config.png   ← Passive scan threshold configuration
    │   └── 03_zap_session_management_alert.png ← Session Management alert
    │
    └── devtools/
        ├── 04_no_https_not_secure.png       ← "Not Secure" browser warning
        ├── 05_no_https_fullpage_view.png    ← Full page view over HTTP
        ├── 06_missing_headers_server_disclosure.png ← Response headers
        ├── 07_cookie_raw_value.png          ← JSESSIONID cookie value
        └── 08_insecure_cookie_flags.png     ← Cookie Secure/HttpOnly flags
```

---

## 🔑 Nmap Findings Summary

| Port | State | Service | Finding |
|---|---|---|---|
| 80/tcp | Open | HTTP | Web application (no HTTPS redirect) |
| 443/tcp | Open | HTTPS | TLS available but not enforced |
| 8080/tcp | Open | http-proxy | Additional web-facing service — unnecessary exposure |
| 8443/tcp | Closed | https-alt | Confirmed closed |

---

## 🍪 Cookie Security Issues (DevTools)

| Cookie | HttpOnly | Secure | Risk |
|---|---|---|---|
| `JSESSIONID` | ✅ true | ❌ false | 🟠 Medium |

---

## 🛡️ Top Remediation Steps

| Priority | Finding | Fix |
|---|---|---|
| 1 | No HTTPS Enforcement | Enforce HTTPS site-wide with a redirect, enable HSTS |
| 2 | Missing Security Headers | Add CSP, X-Frame-Options, X-Content-Type-Options, HSTS |
| 3 | Insecure Cookie | Set `Secure` flag on all session cookies |
| 4 | Server Version Disclosure | Suppress/generalize the `Server` header |
| 5 | Port 8080 Exposed | Restrict to internal access or close if unused |

---

## 📚 Skills Gained

- Vulnerability analysis & risk classification
- Passive web application security testing
- Network scanning & enumeration with Nmap
- Passive scanning with OWASP ZAP
- Security header & cookie analysis with browser DevTools
- Professional security reporting & documentation

---

## 👤 Author

**Kabiraj Chapagain**
Cyber Security Intern — Future Interns

---

*⚠️ Disclaimer: This assessment was conducted for educational purposes as part of the Future Interns Cyber Security Internship. It was strictly limited to passive, read-only techniques against a publicly accessible test target. No exploitation, unauthorized access, or disruption of service was performed or attempted.*
