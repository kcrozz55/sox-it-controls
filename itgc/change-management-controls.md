# SOX ITGC — Change Management Controls (ITGC-CM)

**Document ID:** SOX-CM-001
**Version:** 1.0
**Classification:** Internal
**Owner:** Amara Osei, ISSO
**Approved By:** Linda R. Parker, CFO
**Effective Date:** January 1, 2026
**Assessment Period:** January 1, 2025 – December 31, 2025

---

## Purpose

Change Management IT General Controls ensure that changes to financial reporting systems are authorized, tested, and implemented in a controlled manner. Unauthorized or untested changes to financial applications represent a significant risk to the integrity of financial reporting.

---

## Systems in Scope

| System | Change Frequency | Change Risk |
|--------|-----------------|-------------|
| EHRP Billing Module | High (monthly releases) | High — directly affects revenue recognition |
| QuickBooks Enterprise | Low (annual version upgrade) | Medium — affects general ledger calculations |
| ADP Workforce Now | Vendor-managed | Low — payroll configuration changes only |
| Stripe Payment Platform | Vendor-managed | Low — API integration changes only |

---

## Control ITGC-CM-01: Change Authorization

**Control Objective:** All changes to financial reporting systems are formally authorized by appropriate management prior to implementation.

**Control Description:** All changes to in-scope financial systems must be submitted as change requests in ServiceNow, reviewed by the Change Advisory Board (CAB), and approved by both the IT Change Manager and the CFO (or designee) before implementation in the production environment.

**Control Owner:** Amara Osei, ISSO; Linda R. Parker, CFO

**Key Attributes:**
- Change requests submitted in ServiceNow with business justification, risk assessment, and rollback plan
- Standard changes: IT Change Manager approval required
- Significant changes (financial logic, calculation engine, reporting): CFO approval required in addition to IT Change Manager
- Emergency changes: Post-implementation CFO review required within 2 business days
- No production changes permitted outside the defined change window without emergency change approval

**Testing Evidence (FY2025):**
- Population: 127 changes to in-scope financial systems in FY2025
- Sample: 40 changes selected (31% of population; all significant changes tested)
- Results: 40/40 had documented change request in ServiceNow; 40/40 had IT Change Manager approval; 17/17 significant changes had CFO approval
- 5 emergency changes identified: all 5 had post-implementation CFO review within 2 days
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-CM-02: Change Testing Prior to Implementation

**Control Objective:** Changes to financial reporting systems are tested in a non-production environment before implementation in production to ensure they operate as intended and do not introduce unintended errors.

**Control Description:** All changes to in-scope financial systems must be tested in the QA/staging environment by a tester who is independent of the developer. Test results must be documented and approved before change promotion to production.

**Control Owner:** Thomas J. Bridwell, Systems Administrator

**Key Attributes:**
- Mandatory test environment: No direct development-to-production deployments permitted
- Test cases must include regression testing for financial calculations
- UAT (User Acceptance Testing) by billing or finance staff required for changes affecting financial logic
- QA approval documented in JIRA before production deployment
- Developer who wrote the code cannot be the sole tester

**Testing Evidence (FY2025):**
- Population: 127 changes (same as CM-01)
- Sample: 40 changes (same sample as CM-01)
- Results: 40/40 had documented evidence of pre-production testing; 40/40 had test sign-off from individual independent of developer; 23/23 billing-logic changes had UAT sign-off from finance/billing staff
- 0 instances of direct production deployment without test evidence
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-CM-03: Segregation of Duties in Change Deployment

**Control Objective:** The individual who develops a change is not the same individual who deploys it to the production environment.

**Control Description:** Production deployment access is restricted to a separate deployment team. Developers do not have write access to the production environment. Deployments are executed by the DevOps/Release team using CI/CD pipelines with mandatory approval gates.

**Control Owner:** Keisha M. Robertson, Cloud Security Engineer

**Key Attributes:**
- GitHub branch protection: Pull requests to `main` branch require review from code owner (cannot approve own PR)
- CI/CD pipeline (GitHub Actions) enforces QA approval gate before production deployment
- Developer IAM role: Read-only access to production AWS environment
- Deployment team IAM role: Deploy access only; no code write access
- Separation verified quarterly via access review

**Testing Evidence (FY2025):**
- Developer access roles reviewed: All 6 developers confirmed read-only in production
- Deployment pipeline configuration reviewed: Approval gates confirmed active
- Sample of 25 deployments: 0/25 deployed by the developer who authored the code
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-CM-04: Emergency Change Procedures

**Control Objective:** Emergency changes to financial systems are tracked, reviewed, and approved after-the-fact with appropriate oversight.

**Control Description:** Emergency changes may bypass standard CAB review but must follow an expedited approval process: verbal approval from CISO + CFO, documented immediately in ServiceNow, post-implementation review within 2 business days.

**Control Owner:** Amara Osei, ISSO

**Testing Evidence (FY2025):**
- Population: 5 emergency changes to financial systems in FY2025
- All 5 reviewed (full population)
- Results: 5/5 had CISO verbal approval documented; 5/5 had CFO post-implementation review within 2 days; 5/5 entered into ServiceNow within 4 hours of implementation
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Change Management Summary — FY2025

| Control ID | Control Name | Result | Exceptions |
|------------|-------------|--------|-----------|
| ITGC-CM-01 | Change Authorization | Effective | 0 |
| ITGC-CM-02 | Pre-Implementation Testing | Effective | 0 |
| ITGC-CM-03 | Segregation of Duties in Deployment | Effective | 0 |
| ITGC-CM-04 | Emergency Change Procedures | Effective | 0 |
| **Overall** | | **Effective** | **0** |

---

## Change Volume Statistics — FY2025

| System | Standard Changes | Emergency Changes | Significant Changes (CFO review) |
|--------|-----------------|------------------|----------------------------------|
| EHRP Billing Module | 98 | 4 | 21 |
| QuickBooks Enterprise | 3 | 1 | 2 |
| ADP Workforce Now | 18 | 0 | 0 |
| Stripe Platform | 8 | 0 | 0 |
| **Total** | **127** | **5** | **23** |
