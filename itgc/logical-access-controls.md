# SOX ITGC — Logical Access Controls (ITGC-LA)

**Document ID:** SOX-LA-001
**Version:** 1.0
**Classification:** Internal
**Owner:** Amara Osei, ISSO
**Approved By:** Linda R. Parker, CFO
**Effective Date:** January 1, 2026
**Assessment Period:** January 1, 2025 – December 31, 2025

---

## Purpose

This document documents MedCore Health Systems' IT General Controls for logical access to financial reporting systems. Effective logical access controls ensure that only authorized individuals can access systems that affect the financial statements, and that access is granted based on job requirements (segregation of duties).

---

## Financial Systems in Scope

| System | Access Control Method | MFA Required | Admin Accounts |
|--------|----------------------|--------------|---------------|
| EHRP Billing Module | Okta SSO + RBAC | Yes | 3 admin accounts |
| QuickBooks Enterprise 2026 | Local accounts + AD integration | Yes (VPN) | 2 admin accounts |
| ADP Workforce Now | ADP portal accounts | Yes (built-in) | 1 admin account |
| Stripe Dashboard | Stripe portal + SSO | Yes | 2 admin accounts |

---

## Control ITGC-LA-01: User Access Provisioning

**Control Objective:** Access to financial systems is granted only to authorized users based on documented business need and manager approval.

**Control Description:** All access requests for financial systems must be submitted via ServiceNow, approved by the employee's manager and the CFO (for systems with financial reporting impact), and provisioned by the IT Security team.

**Control Owner:** Carlos Vega, IAM Administrator

**Key Attributes:**
- Access requests require employee's manager approval (Level 1) and CFO approval (Level 2) for all financial system access
- Role-based access: Billing staff have read/create; supervisors have read/create/approve; finance directors have full access
- No access is granted without documented approval in ServiceNow
- Access provisioning timeline: Within 2 business days of dual approval

**Testing Evidence (FY2025):**
- Population: 87 access provisioning events in financial systems during FY2025
- Sample: 25 events selected (29% of population)
- Results: 25/25 had documented manager approval; 25/25 had CFO approval; 25/25 provisioned within 2 business days
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-LA-02: User Access Termination

**Control Objective:** Access to financial systems is revoked promptly when employment terminates or when a user's job function changes.

**Control Description:** HR system (Workday) triggers an automated workflow to disable access in all financial systems within 4 hours of employee separation. Access is also reviewed within 5 business days of any role change.

**Control Owner:** Sharon Bello, HR Director; Amara Osei, ISSO

**Key Attributes:**
- Automated offboarding: HR separation event in Workday triggers Okta deprovisioning
- QuickBooks and ADP accounts disabled within 4 hours by IAM team
- Role change access review: 5-day SLA; access that no longer aligns with new role removed

**Testing Evidence (FY2025):**
- Population: 47 employee terminations in FY2025
- Sample: All 47 reviewed (full population due to criticality)
- Results: 47/47 had financial system access disabled within 4 hours of separation
- 12 role changes reviewed: 12/12 had access adjusted within 5 business days
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-LA-03: Quarterly Access Reviews (User Access Certification)

**Control Objective:** Access to financial systems is reviewed periodically to ensure it remains appropriate and aligned with current job responsibilities.

**Control Description:** The CFO and departmental managers certify all user access to financial systems quarterly via Okta Lifecycle Management. Inappropriate access identified during reviews is revoked within 5 business days.

**Control Owner:** Carlos Vega, IAM Administrator; Linda R. Parker, CFO

**Testing Evidence (FY2025):**
- Q1 2025 review: 94 accounts certified; 3 access entries removed; completed within deadline
- Q2 2025 review: 97 accounts certified; 1 access entry removed; completed within deadline
- Q3 2025 review: 99 accounts certified; 2 access entries removed; completed within deadline
- Q4 2025 review: 101 accounts certified; 4 access entries removed; completed within deadline
- All four quarterly reviews completed on time with appropriate manager and CFO sign-off
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-LA-04: Privileged Access Management

**Control Objective:** Privileged access to financial systems is restricted to a minimal set of authorized administrators and is subject to enhanced oversight.

**Control Description:** Administrative access to financial systems requires CyberArk PAM with session recording. Shared admin accounts are prohibited. Admin activities are logged and reviewed monthly.

**Control Owner:** Amara Osei, ISSO

**Key Attributes:**
- Administrative accounts are separate from standard user accounts
- Admin access requires MFA (hardware token for financial system admins)
- All admin sessions logged in CyberArk with session recording
- Admin access list reviewed monthly; any additions require CISO approval
- 8 admin accounts total across all in-scope financial systems (QuickBooks 2, EHRP Billing 3, ADP 1, Stripe 2)

**Testing Evidence (FY2025):**
- Admin account population: 8 accounts across 4 systems
- All 8 admin accounts verified to have unique credentials (no shared accounts)
- All 8 admin accounts verified as having active CyberArk enrollment
- Monthly admin access reviews: 12/12 completed on time
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-LA-05: Segregation of Duties in Financial Systems

**Control Objective:** No single individual can both initiate and approve a financial transaction that affects the financial statements.

**Control Description:** Role-based access in EHRP Billing Module and QuickBooks enforces segregation of duties between transaction entry, approval, and posting. System-enforced controls prevent a single user from performing all three functions.

**Control Owner:** Linda R. Parker, CFO

**Key Segregation Rules Enforced:**
| Duty 1 | Duty 2 | Segregated? |
|--------|--------|------------|
| Create billing charge | Approve/post billing charge | Yes — separate roles |
| Create vendor invoice | Approve payment | Yes — separate roles |
| Process payroll | Approve payroll | Yes — ADP workflow enforces 2-person approval |
| Create journal entry | Approve journal entry | Yes — separate roles in QuickBooks |

**Testing Evidence (FY2025):**
- SOD matrix reviewed by external auditors (Deloitte); no conflicts identified
- System access report compared to SOD matrix: 0 users with conflicting access
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-LA-06: Password Policy for Financial Systems

**Control Objective:** Authentication credentials for financial systems meet minimum security standards.

**Control Description:** Password policy enforced via Active Directory and Okta: 16-character minimum, complexity requirements, 90-day expiration, no reuse of last 12 passwords. MFA required for all financial system access.

**Testing Evidence (FY2025):**
- Password policy configuration screenshots captured and compared to policy requirements
- MFA enrollment verified: 100% of financial system users enrolled in MFA
- 0 exceptions to password policy identified
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Logical Access Summary — FY2025

| Control ID | Control Name | Result | Exceptions |
|------------|-------------|--------|-----------|
| ITGC-LA-01 | User Access Provisioning | Effective | 0 |
| ITGC-LA-02 | User Access Termination | Effective | 0 |
| ITGC-LA-03 | Quarterly Access Reviews | Effective | 0 |
| ITGC-LA-04 | Privileged Access Management | Effective | 0 |
| ITGC-LA-05 | Segregation of Duties | Effective | 0 |
| ITGC-LA-06 | Password Policy | Effective | 0 |
| **Overall** | | **Effective** | **0** |
