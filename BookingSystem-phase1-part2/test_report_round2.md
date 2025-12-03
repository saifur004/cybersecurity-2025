Booking System – Phase 1 Part 2 Manual Test Report
1️⃣ Introduction
Tester(s):

Saifur Rahman

Punam Thakuri

Purpose

To verify whether the main security and validation issues found in Part 1 were fixed in the updated Booking System registration functionality. The focus was on improved validation, injection protection, and security headers.

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

The updated registration page shows strong improvements. Email validation, password rules, XSS filtering, and SQL injection protections are now functioning correctly. However, CSRF protection is still missing and remains the main unresolved issue.

Overall risk level: Medium

Top 5 immediate actions

Implement CSRF protection tokens

Continue enforcing backend input validation

Ensure all security headers are consistently applied

Add rate limiting to registration requests

Plan for Phase 3 testing after next updates

3️⃣ Severity Scale & Definitions
Severity Level	Description	Recommended Action
🔴 High	A serious vulnerability that can lead to full system compromise or data breach	Immediate fix required
🟠 Medium	Significant issue requiring specific user interaction or conditions	Fix ASAP
🟡 Low	Minor issue or configuration weakness	Fix soon
🔵 Info	No direct risk but helpful for hardening the system	Monitor and fix in maintenance
4️⃣ Findings
ID	Severity	Finding	Description	Evidence / Proof
F-01	🟠 Medium	Missing CSRF protection	No CSRF tokens are implemented in the registration flow.	ZAP alert: “Absence of Anti-CSRF Tokens”
F-02	🔵 Info	Security headers partially configured	Several headers were fixed but CSRF-related protections are still missing.	ZAP scan results
F-03	🔵 Info	Backend depends heavily on form structure	Input validation depends strongly on frontend patterns; backend could use additional sanitization.	Manual test observations

Note:
All major issues from Part 1 (Email validation, Password strength, XSS, SQL Injection) are fixed and therefore not repeated here.

5️⃣ OWASP ZAP Test Report (Attachment)
Purpose

To document automated security scanning performed on Part 2 of the Booking System.

Commands used (Target: localhost:8001)
zap-baseline.py -t http://localhost:8001 -r zap_report_round1.html -J zap_report_round1.json

zap-cli report -o zap_report_round2.md -f markdown

Report file (GitHub link)

📁 ZAP Report:
https://github.com/saifur004/cybersecurity-2025/blob/main/BookingSystem-phase1-part2/zap_report_round2.md