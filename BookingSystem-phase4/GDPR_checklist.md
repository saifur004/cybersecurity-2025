# GDPR Compliance Checklist – Web-based Booking System (Phase 4)

## Result: Personal Data Mapping and Minimization

| Check | Result | Notes |
|-------|--------|-------|
| Identified personal data (e.g., name, email, age, username) | ✅ | Personal data identified in `booking_users`: username (email), birthdate, role, user_token |
| Only necessary personal data collected (data minimization) | ✅ | No address, phone number, or unnecessary identifiers collected |
| User age recorded to verify that the booker is over 15 years old | ✅ | Birthdate stored and used only for age verification via database trigger |

---
![alt text](<Screenshot 2025-12-15 163849.png>)

## Result: User Registration and Management

| Check | Result | Notes |
|-------|--------|-------|
| Registration includes GDPR-compliant consent (privacy/terms acceptance) | ⚠️ | `terms_accepted` flag exists, but policy pages were initially empty |
| Users can view and edit their personal data | ⚠️ | Users can view account details, but self-deletion is not available |
| Administrator can delete a reserver (right to be forgotten) | ✅ | Admin deletion supported; cascading delete removes related reservations |
| Underage registration/booking (under 15) restricted | ✅ | Age check enforced via database trigger before reservation |

---
![alt text](<Screenshot 2025-12-15 164241.png>)

## Result: Booking Visibility

| Check | Result | Notes |
|-------|--------|-------|
| Bookings visible to non-logged-in users only at resource level | ✅ | Public users see resource and time only |
| Personal data not exposed publicly or to unauthorized users | ⚠️ | Logged-in users can see reserver email, violating data minimization |

---
![alt text](<Screenshot 2025-12-15 164456.png>)

## Result: Access Control and Authorization

| Check | Result | Notes |
|-------|--------|-------|
| Only administrators can manage resources and reservations | ✅ | Role-based restrictions enforced |
| Role-based access control implemented | ✅ | Roles stored and enforced (`reserver`, `administrator`) |
| Administrator privileges limited to GDPR-compliant use | ⚠️ | No technical restriction preventing admins from viewing personal data |

---

## Result: Privacy by Design Principles

| Check | Result | Notes |
|-------|--------|-------|
| Privacy by Default implemented | ✅ | Minimal data collected by default |
| Logs implemented without unnecessary personal data | ⚠️ | Login/admin logs exist; retention policy not defined |
| Forms and system components designed with data protection in mind | ✅ | Secure login, hashed passwords, minimal fields |

---

## Result: Data Security

| Check | Result | Notes |
|-------|--------|-------|
| CSRF, XSS, SQL injection protections implemented | ⚠️ | Not fully verified during testing |
| Passwords securely hashed | ✅ | `password_hash` stored, no plaintext passwords |
| Data backup and recovery GDPR-compliant | ⚠️ | Backup and retention not documented |
| Personal data stored within EU | ⚠️ | Hosting location not verified |

---

## Result: Data Anonymization and Pseudonymization

| Check | Result | Notes |
|-------|--------|-------|
| Personal data anonymized where possible | ⚠️ | Email shown to logged-in users |
| Pseudonymization techniques used | ✅ | `user_token` UUID used instead of email in reservations |

---

## Result: Data Subject Rights

| Check | Result | Notes |
|-------|--------|-------|
| Users can download/request all personal data | ❌ | No data export or access request feature |
| Users can request deletion of personal data | ⚠️ | Admin can delete users; no user-initiated process |
| Users can withdraw consent | ❌ | No mechanism to withdraw consent after registration |

---

## Result: Documentation and Communication

| Check | Result | Notes |
|-------|--------|-------|
| Privacy policy available and accessible | ❌ | Policy pages existed but were empty during testing |
| Admins/developers provided with data protection documentation | ⚠️ | Not observed in system |
| Documented data breach response process | ❌ | No breach response documentation available |

---

## Summary

### Compliance Status Legend
- ✅ **Compliant** – Requirement fully met
- ⚠️ **Partial** – Requirement partially met or concerns identified
- ❌ **Non-compliant** – Requirement not met

### Overall Assessment
The Booking System demonstrates strong technical implementation of core GDPR principles (data minimization, secure storage, role-based access). However, critical gaps exist in user rights implementation (data export, self-deletion, consent withdrawal) and documentation (privacy policies, breach response procedures).