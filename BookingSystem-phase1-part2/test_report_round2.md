Booking System – Phase 1 Part 2 Manual Test Report
1️⃣ Introduction

Tester(s):
Name: Saifur Rahman
Name: Punam Thakuri

Purpose:
To verify whether the main security and validation issues found in Part 1 were fixed in the updated Booking System registration functionality. The goal was to test improved validation, injection protection, and security headers.

Scope:

Tested components:

Registration page (email, password, input sanitization, backend validation)

Security headers via ZAP

Exclusions:

Login flow

Database design

Booking functionality

Admin pages

Test approach:
Black-box (manual testing + ZAP scanning)

Test environment & dates:

Start: 11.12.2025

End: 11.12.2025

Environment details:

OS: Windows

Browser: Firefox (ZAP built-in)

Runtime: Localhost server running at http://localhost:8000

Tools: OWASP ZAP, browser developer tools

Assumptions & constraints:

Only the registration page was provided for testing

No server code access

Password rules controlled by server logic


2️⃣ Executive Summary

The updated registration page shows major improvements. Email validation, password validation, XSS filtering, and SQL injection protections are now working correctly. One issue remains: the system still lacks CSRF protection.

Overall risk level: Medium

Top 5 immediate actions:

Implement CSRF protection tokens

Continue enforcing backend input validation

Apply complete security headers consistently

Add rate limiting for registration requests

Conduct Phase 3 testing once fixes are deployed

3️⃣ Severity scale & definitions
Severity Level	Description	Recommended Action
🔴 High	A serious vulnerability that can lead to full system compromise or data breach	Immediate fix required
🟠 Medium	A significant issue requiring specific conditions or interaction	Fix ASAP
🟡 Low	Minor issue or configuration weakness	Fix soon
🔵 Info	No direct risk but useful for system hardening	Monitor and fix in maintenance
4️⃣ Findings
ID	Severity	Finding	Description	Evidence / Proof
F-01	🟠 Medium	Missing CSRF protection	ZAP reports absence of anti-CSRF tokens. No CSRF tokens are included in registration form.	ZAP alert: “Absence of Anti-CSRF Tokens”
F-02	🔵 Info	Security headers partially configured	Some headers from Part 1 were fixed but CSRF-related protections still missing.	ZAP scan results
F-03	🔵 Info	Backend depends heavily on form structure	Validation relies on strict patterns but would benefit from additional sanitization steps.	Manual test observations
Note

All major issues from Part 1 (Email validation, password strength, XSS, SQL injection) are fixed, so they are not listed again as findings.

5️⃣ OWASP ZAP Test Report (Attachment)

Purpose:
To document automated security scanning performed on Part 2 of the Booking System.

Commands used (localhost:8001)
zap-baseline.py -t http://localhost:8001 -r zap_report_round1.html -J zap_report_round1.json
zap-cli report -o zap_report_round2.md -f markdown

Report file

Attach or link your final ZAP report here:

📁 ZAP Report:
https://github.com/saifur004/cybersecurity-2025/blob/main/BookingSystem-phase1-part2/zap_report_round2.md