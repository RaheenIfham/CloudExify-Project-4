# CloudExify Project 4 — Vulnerability Assessment & Remediation

**CloudExify Summer Internship 2026 — Cybersecurity, Month 2 (Final Project)**

## Overview

This project is a full Vulnerability Assessment (VA) of a local web application environment, combining automated scanning with manual security testing to identify, confirm, score, and remediate real vulnerabilities. It builds directly on the manual penetration testing work from [Project 3](https://github.com/RaheenIfham/CloudExify-Project-3), re-validating those findings alongside new infrastructure-level issues discovered through automated scanning.

**Target environment:** Localhost XAMPP stack (Apache, PHP, MariaDB) running DVWA (Damn Vulnerable Web Application), scoped strictly to `127.0.0.1` — no external hosts or devices were tested.

## Objective

To identify vulnerabilities in the target environment, assess their severity and potential business impact using CVSS scoring, and provide actionable remediation recommendations to reduce risk before exploitation.

## Methodology

The assessment followed a structured 15-day plan across six phases:

1. **Planning** — scope, objectives, timeline definition
2. **Reconnaissance** — baseline enumeration of open ports and software versions
3. **Scanning** — automated vulnerability scanning with Nessus Essentials (network + web application)
4. **Enumeration** — cross-referencing scan results against verified installed versions
5. **Vulnerability Analysis** — manual validation of exploitability, followed by CVSS v3.1 scoring
6. **Reporting** — remediation planning and final report assembly

## Tools Used

- **Nessus Essentials 10.12.3** — automated vulnerability scanning
- **DVWA** — intentionally vulnerable web application (target)
- **XAMPP** — Apache, PHP, MariaDB stack (target infrastructure)
- **Burp Suite Community Edition** — carried over from Project 3, used for brute-force evidence
- **Command line tools** — `netstat`, `httpd -v`, `mysql --version`, `openssl version` for manual enumeration

## Key Findings

| # | Finding | Severity | CVSS |
|---|---|---|---|
| 1 | Unrestricted File Upload → Remote Code Execution | Critical | 9.9 |
| 2 | OS Command Injection | Critical | 9.9 |
| 3 | Outdated Apache Web Server (2.4.58) | Critical | 9.8 |
| 4 | Outdated PHP (8.2.12) | Critical/High | varies |
| 5 | SQL Injection | High | 7.7 |
| 6 | No Account Lockout (Brute Force) | High | 7.1 |
| 7 | Cross-Site Request Forgery (CSRF) | Medium | 6.5 |
| 8 | Reflected Cross-Site Scripting (XSS) | Medium | 6.1 |
| 9 | Stored Cross-Site Scripting (XSS) | Medium | 5.4 |
| 10 | Outdated OpenSSL (3.1.3) | Low–Medium | — |

**10 vulnerabilities confirmed** — 4 Critical, 3 High, 3 Medium/Low.

## Notable Insight

Nessus's automated web application scan did **not** independently detect DVWA's intentional application-layer vulnerabilities (SQL Injection, XSS, CSRF, Command Injection, File Upload). These were only identified through manual testing (originally in Project 3, re-validated here in Days 8–9). Nessus was, however, effective at catching infrastructure-level issues — outdated Apache, PHP, and OpenSSL versions — based on self-reported version detection rather than active exploitation. This reinforced that automated scanning and manual testing are complementary, not interchangeable, and both are necessary for a complete assessment.

## Repository Contents

| File / Folder | Description |
|---|---|
| `vulnerability_assessment_report.pdf` | Final formal report — Executive Summary, Findings Summary, Detailed Technical Findings, Remediation Roadmap, Testing Methodology, Appendices |
| `Project4_Daily_Log.docx` | Full day-by-day working log (Days 1–15) with predictions, results, and notes |
| `screenshots/` | All evidence screenshots (Nessus scans, manual validation) with captions in `README.md` |

## Remediation Summary

| Priority | Timeline | Findings |
|---|---|---|
| Critical | 0–24 hours | File Upload/RCE, Command Injection, Outdated Apache |
| High | 1–7 days | SQL Injection, Brute Force, Outdated PHP |
| Medium | 1–30 days | CSRF, Reflected XSS, Stored XSS, Outdated OpenSSL |

Full remediation steps, effort estimates, and root-cause analysis for each finding are documented in the final report.

## Related Repositories

- [CloudExify-Project-3](https://github.com/RaheenIfham/CloudExify-Project-3) — Manual Web Application Penetration Testing (source of the original DVWA findings re-validated in this project)

---
*CloudExify Cybersecurity Internship — Month 2, Final Project*
