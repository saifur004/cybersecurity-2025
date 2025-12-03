Booking System – Phase 1 Part 2 Manual Test Report
1️⃣ Introduction
Tester(s)

Saifur Rahman

Punam Thakuri

Purpose

To verify whether the main security and validation issues found in Part 1 were fixed in the updated Booking System registration functionality.
Testing focused on improved validation, injection protection, and security headers.

Scope

Tested components:

Registration page (email validation, password validation, input sanitization, backend validation)

Security headers via OWASP ZAP

Exclusions:

Login flow

Database design

Booking functionality

Admin pages

Test approach

Black-box testing

Manual testing

Automated scanning using OWASP ZAP

Test environment & dates

Start: 11.12.2025

End: 11.12.2025

Environment details

OS: Windows

Browser: Firefox (ZAP built-in browser)

Runtime: Localhost server at http://localhost:8001

Tools: OWASP ZAP, browser developer tools

Assumptions & constraints

Only the registration page was provided for testing

No server code access

Password rules enforced by backend logic

2️⃣ Executive Summary

The updated registration page shows strong improvements.
Email validation, password validation, XSS filtering, and SQL injection protections now function correctly.

However, CSRF protection is still missing and remains the primary unresolved issue.

Overall risk level: Medium

Top 5 immediate actions

Implement CSRF protection tokens

Continue enforcing backend input validation

Ensure all security headers are consistently applied

Add rate limiting to registration requests

Plan for Phase 3 retesting once fixes are deployed

3️⃣ Severity Scale & Definitions
| Severity Level | Description                                                                    | Recommended Action             |
| -------------- | ------------------------------------------------------------------------------ | ------------------------------ |
| 🔴 High        | A serious vulnerability that can lead to full system compromise or data breach | Immediate fix required         |
| 🟠 Medium      | Significant issue requiring specific user interaction or conditions            | Fix ASAP                       |
| 🟡 Low         | Minor configuration issue or weakness                                          | Fix soon                       |
| 🔵 Info        | No direct risk but useful for system hardening                                 | Monitor and fix in maintenance |

4️⃣ Findings
| ID       | Severity  | Finding                                   | Description                                                                    | Evidence / Proof                         |
| -------- | --------- | ----------------------------------------- | ------------------------------------------------------------------------------ | ---------------------------------------- |
| **F-01** | 🟠 Medium | Missing CSRF protection                   | No CSRF tokens implemented in registration flow                                | ZAP alert: “Absence of Anti-CSRF Tokens” |
| **F-02** | 🔵 Info   | Security headers partially configured     | Some headers improved but CSRF-related headers missing                         | ZAP scan results                         |
| **F-03** | 🔵 Info   | Backend depends heavily on form structure | Validation relies heavily on frontend patterns; backend could sanitize further | Manual test observations                 |



Note:
All major issues from Part 1 (Email validation, password strength, XSS, SQL Injection) are fixed, so they are not repeated here.

5️⃣ OWASP ZAP Test Report (Attachment)
Purpose

To document the automated security scan performed with OWASP ZAP on the updated registration page.

Commands used (Target: localhost:8001)
zap-baseline.py -t http://localhost:8001 -r zap_report_round1.html -J zap_report_round1.json

zap-cli report -o zap_report_round2.md -f markdown

Report file (GitHub link)

📁 ZAP Report:
https://github.com/saifur004/cybersecurity-2025/blob/main/BookingSystem-phase1-part2/zap_report_round2.md