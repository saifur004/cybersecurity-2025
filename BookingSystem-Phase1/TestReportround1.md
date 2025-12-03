Booking System – Phase 1 Test Report
1️⃣ Introduction
Tester(s):

Saifur Rahman

Punam Thakuri

Purpose

To identify validation weaknesses, usability problems, and security vulnerabilities in the registration process of the Booking System during Phase 1 testing.

Scope

Tested components:

Registration page (input validation, server response behavior, basic security controls)

Exclusions:

Login

Booking flow

Admin dashboard

API endpoints

Payment modules

Test approach:

Black-box testing using manual testing and OWASP ZAP automated scanning

Test environment & dates

Start: 27.11.2025

End: 27.11.2025

Environment details

Target: http://localhost:8000

Tools: Firefox (ZAP browser), OWASP ZAP, browser developer tools

Environment: Local assignment environment

Assumptions & constraints

Only the registration page was available for testing

No server code access

Browser validation handled on frontend, backend behavior tested via submissions

Limited time and restricted test scope

2️⃣ Executive Summary

Phase 1 testing revealed several weaknesses in the registration flow.
The application relies heavily on client-side validation and lacks strong backend checks for:

Email format

Password strength

Birthdate validation

Potentially dangerous inputs

OWASP ZAP scanning also showed missing security headers.

Overall risk level: Medium

Top 5 immediate actions

Add backend input validation and sanitization

Enforce a strong password policy

Reject invalid or future birthdates

Add essential security headers (CSP, X-Frame-Options, X-Content-Type-Options)

Reduce reliance on browser validation; enforce checks server-side

3️⃣ Severity scale & definitions
Severity Level	Description	Recommended Action
🔴 High	Serious vulnerability that may compromise data or system integrity	Immediate fix
🟠 Medium	Significant issue requiring some conditions to exploit	Fix soon
🟡 Low	Minor weakness or configuration issue	Fix in development cycle
🔵 Info	No direct exploit but helpful for improving security	Monitor and improve
4️⃣ Findings
ID	Severity	Finding	Description	Evidence / Proof
F-01	🔴 High	Missing server-side input validation	Registration accepts SQL-like strings and script-like text without sanitization	Accepted ' OR 1=1 -- in password field
F-02	🟠 Medium	Weak password policy	Very short passwords (e.g., “123”) are accepted	Registration succeeded with “123”
F-03	🟠 Medium	Invalid or future birthdates allowed	Future dates are allowed without backend checks	Registration completed with a future birthdate
F-04	🟠 Medium	Email validated only by browser	Backend did not validate email format	Input “abc” only triggered browser validation
F-05	🟡 Low	Missing security headers	ZAP detected missing CSP, X-Frame-Options, X-Content-Type-Options	Listed in ZAP alerts
5️⃣ OWASP ZAP Test Report (Attachment)

The automated security scan was performed using OWASP ZAP.
It identified missing security headers and weak input validation.

Commands Used

Baseline scan:

zap-baseline.py -t http://localhost:8000 -r test_report.html -J zap_report_round1.json


Export Markdown report:

zap-cli report -o zap_report_round1.md -f markdown

Attached Report

📁 Full ZAP Report:
https://github.com/saifur004/cybersecurity-2025/blob/main/BookingSystem-Phase1/ZAP-report.md

Conclusion

The registration page functions correctly but lacks essential security protections such as robust server-side validation and complete security headers.
These issues should be addressed in Phase 2 to ensure improved reliability and security.