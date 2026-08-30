# CloudExify Project 4 — Screenshots

Vulnerability Assessment & Remediation (Cybersecurity, Month 2)

Evidence screenshots extracted from `Project4_Daily_Log.docx`, listed in day order with captions.

---

**Day02_01_netstat_ports_listening.png**
`netstat` output confirming ports 80 (Apache) and 3306 (MySQL/MariaDB) listening on IPv4 and IPv6.

**Day02_02_apache_mysql_php_versions.png**
Command-line verification of Apache, MariaDB, and PHP versions.

**Day03_01_nessus_dashboard_ready.png**
Nessus dashboard confirming plugin compilation complete and scanner ready.

**Day04_01_scan_summary_hosts.png**
Network scan summary: 7 Critical, 10 High, 16 Medium, 129 Low/Info findings.

**Day04_02_vulnerabilities_by_family.png**
Vulnerabilities grouped by category/family.

**Day04_03_remediations_tab.png**
Nessus-recommended fixes: Apache, PHP, OpenSSL upgrades.

**Day04_04_network_interface_note.png**
Scan note: network interface does not support packet forgery (methodology limitation).

**Day04_05_history_tab.png**
Scan history/details panel.

**Day04_06_critical_high_findings.png**
Individual Critical (CVSS 9.8) and High (CVSS 7.5) findings, sorted.

**Day04_07_apache_critical_cve_detail.png**
Detailed CVE breakdown for Apache 2.4.x < 2.4.67 (4 bundled CVEs).

**Day04_08_history_tab_duplicate.png**
Duplicate view of scan history/details.

**Day05_01_invalid_target_error.png**
Initial misconfiguration — invalid target format (URL instead of IP).

**Day05_02_web_app_config_settings.png**
Corrected scan configuration — crawl settings under Assessment tab.

**Day05_03_scan_running.png**
Web application scan in progress.

**Day05_04_scan_summary_hosts.png**
Web app scan summary: 7 Critical, 9 High, 10 Medium, 88 Low/Info findings.

**Day05_05_vulnerabilities_list.png**
Vulnerabilities grouped by family.

**Day05_06_remediations_tab.png**
Remediation recommendations (matches Day 4: Apache, PHP, OpenSSL).

**Day05_07_notes_network_interface.png**
Repeated network interface limitation note.

**Day05_08_critical_high_web_servers.png**
Critical/High findings under "Web Servers" family.

**Day05_09_apache_2467_critical_detail.png**
Apache 2.4.x < 2.4.67 Critical detail (same issue as Day 4).

**Day05_10_apache_2459_high_detail.png**
Apache 2.4.x < 2.4.59 High detail — includes Nessus's version-only detection disclaimer.

**Day05_11_cgi_abuses_findings.png**
PHP-related Critical/High/Medium findings under "CGI abuses" family.

**Day06_01_version_comparison_table.png**
Apache/PHP/MariaDB/OpenSSL vs. Nessus-flagged thresholds comparison table.

**Day06_02_openssl_version_check.png**
Command-line verification of OpenSSL version (3.1.3).

**Day08_01_file_upload_success.png**
DVWA confirms successful upload of test PHP file.

**Day08_02_rce_confirmed_output.png**
Uploaded file executes on the server, confirming Remote Code Execution.

**Day08_03_command_injection_hostname.png**
Command injection payload reveals server hostname.

**Day08_04_command_injection_full_output.png**
Full ping + injected command output.

**Day09_01_sql_injection_all_users.png**
SQL Injection payload dumps all 5 user records.

**Day09_02_sql_injection_duplicate.png**
Duplicate view of SQL Injection result.

**Day09_03_csrf_html_file_notepad.png**
Hidden CSRF attack file (`csrf_validate_day9.html`) contents.

**Day09_04_csrf_blank_page_executed.png**
Blank page shown when CSRF attack file is opened (attack runs silently).

**Day09_05_csrf_login_success_confirmation.png**
Successful login with the attacker-set password, confirming CSRF worked.

**Day10_01_cvss_scores_table.png**
Final CVSS v3.1 scores for all manually validated vulnerabilities.

---

## Summary of Confirmed Vulnerabilities

| Finding | Severity | CVSS |
|---|---|---|
| Unrestricted File Upload → RCE | Critical | 9.9 |
| OS Command Injection | Critical | 9.9 |
| Outdated Apache Web Server | Critical | 9.8 |
| Outdated PHP | Critical/High | varies |
| SQL Injection | High | 7.7 |
| No Account Lockout (Brute Force) | High | 7.1 |
| Cross-Site Request Forgery (CSRF) | Medium | 6.5 |
| Reflected XSS | Medium | 6.1 |
| Stored XSS | Medium | 5.4 |
| Outdated OpenSSL | Low–Medium | — |

Full technical details, proof-of-concept payloads, and remediation steps are documented in `Project4_Daily_Log.docx` and `vulnerability_assessment_report.pdf`.
