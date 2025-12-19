# PortSwigger Proof of Completed Labs

I completed a total of **18 labs** on PortSwigger Web Security Academy. A screenshot of the dashboard showing completed labs is included as proof of completion. The dashboard view clearly demonstrates progress across multiple vulnerability categories aligned with the OWASP Top 10.
![alt text](image.png)
## Completed Labs List

### SQL Injection
- SQL Injection → WHERE clause allows retrieval of hidden data
- SQL Injection → Login bypass
- SQL Injection → Union-based SQL injection
- SQL Injection → Authentication bypass via SQL injection

### Authentication
- Authentication → Username enumeration via response differences
- Authentication → Password reset logic flaw
- Authentication → Broken brute-force protection
- Authentication → 2FA simple bypass
- Authentication → Password-based login vulnerable to SQL injection

### Access Control
- Access Control → Unprotected admin functionality
- Access Control → Insecure direct object reference (IDOR)
- Access Control → User role modification via IDOR
- Access Control → Horizontal privilege escalation
- Access Control → Vertical privilege escalation
- Access Control → Method-based access control bypass
- Access Control → URL-based access restriction bypass

### Business Logic
- Business Logic → Excessive trust in client-side controls
- Business Logic → Low-level logic flaw exploitation

These labs helped build hands-on understanding of real-world web application vulnerabilities and common developer mistakes.

---

## The Booking System Project

### Phase 1

**Description:**  
Phase 1 focused on understanding the application and performing baseline security testing. I carried out manual tests on authentication, input validation, and session handling, supported by initial OWASP ZAP scans.

**What worked:**  
Manual testing was effective in identifying obvious vulnerabilities such as missing access restrictions and weak validation. ZAP helped highlight potential risk areas.

**What didn't work:**  
Automated scanning alone did not detect logic flaws or authorization issues.

**What took the most time:**  
Carefully documenting each vulnerability with clear reproduction steps.

**What I learned:**  
Automated tools are useful for discovery, but meaningful results require manual analysis.

---

### Phase 2

**Description:**  
In Phase 2, I performed advanced security testing. This included privilege escalation attempts, SQL injection and XSS payload testing, request interception using OWASP ZAP, password hash extraction, and cracking hashes with John the Ripper.

**What worked:**  
Intercepting and modifying HTTP requests exposed serious backend logic flaws and improper trust in client-side data.

**What didn't work:**  
Some payloads required repeated tuning due to partial backend filtering.

**What took the most time:**  
Validating extracted password hashes and confirming successful cracking.

**What I learned:**  
Even small security misconfigurations can lead to complete system compromise.

---

### Phase 3

**Description:**  
Phase 3 concentrated on authorization and role-based access control. I tested user roles, manipulated URLs manually, reviewed exposed endpoints, ran passive scans, and assessed GDPR-related data exposure.

**What worked:**  
Manual role switching and endpoint analysis successfully revealed authorization weaknesses.

**What didn't work:**  
Passive scanning was not sufficient for detecting business logic vulnerabilities.

**What took the most time:**  
Mapping permissions and access boundaries between different user roles.

**What I learned:**  
Authorization flaws often pose a higher risk than injection vulnerabilities.

---

### Phase 4

**Description:**  
The final phase focused on GDPR compliance and Privacy by Design. I reviewed data handling practices, created a GDPR checklist, and authored Privacy Policy, Terms of Service, and Cookie Policy documents.

**What worked:**  
Using a structured GDPR framework ensured that all major compliance areas were reviewed.

**What didn't work:**  
Several privacy-related requirements were missing from the original system design.

**What took the most time:**  
Writing clear and compliant policy documents.

**What I learned:**  
Security and privacy must be integrated from the design stage, not added afterward.

---

## Final Reflection

Throughout this course, I developed a strong practical understanding of web application security. The PortSwigger labs provided hands-on experience with common vulnerabilities, while the booking system project demonstrated how these issues appear in real applications.

I learned that automated tools are valuable but insufficient without manual testing and critical thinking. Access control and authorization testing proved especially important.

Overall, this course significantly improved my confidence in identifying, analyzing, and documenting security vulnerabilities in a structured and professional manner.

---

## Logbook Git Repository

**Repository URL:**  
[https://github.com/saifur004/cybersecurity-2025](https://github.com/saifur004/cybersecurity-2025)

---

## Time Tracking Summary

**Total Hours:** 93 hours

### Hours per Topic:
- Course modules and exam: **14.5 hours**
- PortSwigger Academy labs: **18 hours**
- Booking System Phase 1: **20 hours**
- Booking System Phase 2: **8 hours**
- Booking System Phase 3: **10 hours**
- Booking System Phase 4: **5 hours**
- Additional labs and exercises: **17.5 hours**

---

## Feedback (Optional)

The course was well-structured and balanced between theory and practice. The booking system project was especially valuable because it simulated real-world security testing rather than isolated exercises. More guided examples on advanced authorization testing would further improve the learning experience.