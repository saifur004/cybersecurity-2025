Booking System – Phase 1 Part 2 Manual Test Report
Author: Punam and Saifur
Date: December 2025
1. Purpose of This Report

This report documents the manual penetration and functionality tests performed on the updated Booking System (Phase 1 – Part 2).
The goal was to:

Re-test the registration page

Verify whether the Top 5 issues from Part 1 were fixed

Document the behaviour

Provide screenshots (in Moodle post)

2. Tests Performed in Part 2

Below are the tests performed only on Part 2 of the assignment.

Test 1 – Email Validation
Goal

Check if email validation works properly.

Steps

Tested multiple bad and good email values:

Input	Expected	Actual (Part 2)
abc	Reject	Rejected
abc@	Reject	Rejected
abcabc@@gmail.com	Reject	Rejected
<script>alert(1)</script>	Reject	Rejected
12@gmail.com	Accept	Accepted
Conclusion

✔ Email validation works correctly.
Status: FIXED

Test 2 – Password Validation
Goal

Verify whether password rules are enforced.

Steps

Tested weak, short, and valid passwords.

Password	Expected	Actual
123	Reject	Rejected
abcd123	Reject	Rejected
1234567	Reject	Rejected
Password1!	Accept	Accepted
Conclusion

✔ Password validation is strong.
Status: FIXED

Test 3 – XSS Injection
Goal

Check if user inputs are sanitized to prevent XSS.

Payload Used
<script>alert(1)</script>

Result

Application rejects the payload

XSS does not execute

Conclusion

✔ XSS vulnerability is fixed.
Status: FIXED

Test 4 – SQL Injection Attempt
Goal

Check if backend is vulnerable to SQL injection.

Payload
' OR 1=1--

Method

Inserted payload into the password field using ZAP Requester.

Result

Registration fails normally

No SQL errors

No bypass

Application blocks payload due to password rules

Conclusion

✔ SQL Injection appears mitigated.
Status: FIXED

Test 5 – Security Headers (ZAP)
Goal

Identify security header issues using ZAP.

Part 2 Result (Actual)

Only one alert appeared in ZAP:

❗ “Absence of Anti-CSRF Tokens”
Conclusion

✖ CSRF is still missing
✔ Other major header issues from Part 1 appear fixed

Status: NOT FIXED

3. Summary of Fix Status (Part 2)
Issue Tested	Status
Email validation	Fixed
Password validation	Fixed
XSS	Fixed
SQL Injection	Fixed
Security headers	Partially Fixed
CSRF protection	Not Fixed
4. Final Conclusion

The updated Booking System (Part 2) shows clear improvements.
Most core vulnerabilities from Part 1 have been fixed:

Email validation

Password rules

XSS

SQL Injection

However, one important issue remains:

🚨 CSRF protection is still missing

This should be the next priority for the development team.