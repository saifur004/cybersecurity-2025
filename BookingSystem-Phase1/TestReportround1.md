Booking System – Phase 1 Test Report
1️⃣ Introduction
Tester(s)

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

Tools used: Firefox (ZAP browser), OWASP ZAP, browser developer tools

Environment: Local environment provided for the assignment

Assumptions & constraints

Only the registration page was available for testing

No server code access

Browser validation visible; backend validation tested through form submissions

Limited time and restricted test scope

2️⃣ Executive Summary

Phase 1 testing revealed several weaknesses in the registration flow. The system relies heavily on browser-based validation and lacks strong server-side checks for:

Email format

Password strength

Birthdate validation

Dangerous input handling

OWASP ZAP scanning also showed missing security headers.

Overall risk level: Medium

Top 5 immediate actions

Add backend input validation and sanitization

Enforce a strong password policy

Validate birthdates and reject future dates

Add essential security headers (CSP, X-Frame-Options, X-Content-Type-Options)

Reduce reliance on browser validation; enforce backend checks
3️⃣ Severity scale & definitions
| Severity  | Description                                                        | Recommended Action       |
| --------- | ------------------------------------------------------------------ | ------------------------ |
| 🔴 High   | Serious vulnerability that may compromise data or system integrity | Immediate fix            |
| 🟠 Medium | Significant issue requiring some conditions to exploit             | Fix soon                 |
| 🟡 Low    | Minor weakness or configuration issue                              | Fix in development cycle |
| 🔵 Info   | No direct exploit but helpful for improving security               | Monitor and improve      |


4️⃣ Findings
| ID       | Severity  | Finding                              | Description                                                                     | Evidence / Proof                               |
| -------- | --------- | ------------------------------------ | ------------------------------------------------------------------------------- | ---------------------------------------------- |
| **F-01** | 🔴 High   | Missing server-side input validation | Registration accepts SQL-like strings and script-like text without sanitization | Accepted `' OR 1=1 --` in password field       |
| **F-02** | 🟠 Medium | Weak password policy                 | Very short passwords such as “123” are accepted                                 | Registration succeeded with “123”              |
| **F-03** | 🟠 Medium | Invalid or future birthdates allowed | Backend does not reject future dates                                            | Registration completed with a future birthdate |
| **F-04** | 🟠 Medium | Email validated only by browser      | No backend email validation performed                                           | “abc” only triggered browser validation        |
| **F-05** | 🟡 Low    | Missing security headers             | CSP, X-Frame-Options, and X-Content-Type-Options are missing                    | ZAP security alerts                            |

5️⃣ OWASP ZAP Test Report (Attachment)

The automated security scan was performed using OWASP ZAP. It identified missing headers and weak backend validation.

Commands Used
Baseline scan:
zap-baseline.py -t http://localhost:8000 -r test_report.html -J zap_report_round1.json

Export scan results to Markdown:
zap-cli report -o zap_report_round1.md -f markdown

Attached Report

📁 Full ZAP Report:
https://github.com/saifur004/cybersecurity-2025/blob/main/BookingSystem-Phase1/zap_report_round1.md

Conclusion

The registration page works functionally but lacks strong server-side validation and essential security protections. These findings should be addressed in Phase 2 to improve reliability and reduce security risks.
