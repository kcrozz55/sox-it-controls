# Annual IT General Controls Assessment Report — FY2025

**Document ID:** SOX-ASSESS-001
**Assessment Period:** January 1, 2025 – December 31, 2025
**Report Date:** February 15, 2026
**Classification:** Confidential
**Prepared By:** Amara Osei, ISSO (IT Audit Coordinator)
**Reviewed By:** Jonathan E. Steele, CISO
**Approved By:** Linda R. Parker, CFO
**External Auditor:** Deloitte & Touche LLP (financial statement audit engagement)

---

## 1. Executive Summary

MedCore Health Systems conducted its annual IT General Controls (ITGC) assessment for the fiscal year ended December 31, 2025. The assessment covered 36 controls across four ITGC domains: Logical Access, Change Management, Computer Operations, and Program Development.

**Overall Assessment Conclusion: IT GENERAL CONTROLS ARE EFFECTIVE**

| ITGC Domain | Controls Assessed | Effective | Deficiencies | Material Weakness |
|------------|------------------|-----------|-------------|------------------|
| Logical Access (ITGC-LA) | 6 | 6 | 0 | None |
| Change Management (ITGC-CM) | 4 | 4 | 0 | None |
| Computer Operations (ITGC-CO) | 5 | 4 | 1 (minor) | None |
| Program Development (ITGC-PD) | 3 | 3 | 0 | None |
| **Total** | **18** | **17** | **1** | **None** |

The one minor deficiency identified in Computer Operations (escalation delay in June 2025) was remediated in August 2025 and did not recur in the second half of FY2025.

**Management Conclusion:** Based on the results of this assessment, management concludes that MedCore's IT General Controls over financial reporting were effective throughout FY2025. There are no material weaknesses or significant deficiencies to report.

---

## 2. Assessment Scope and Objectives

### 2.1 Objectives

1. Evaluate the design and operating effectiveness of ITGCs over financial reporting systems
2. Identify control deficiencies, significant deficiencies, or material weaknesses
3. Provide management with assurance over the reliability of financial reporting supported by IT systems
4. Support the external audit engagement with Deloitte & Touche LLP

### 2.2 Systems in Scope

| System | Relevance to Financial Reporting |
|--------|----------------------------------|
| EHRP v4.2.1 — Billing Module | Revenue recognition; accounts receivable |
| QuickBooks Enterprise 2026 | General ledger; financial reporting; AP/AR |
| ADP Workforce Now | Payroll; compensation expense |
| Stripe Payment Platform | Revenue collection; bank reconciliation |

### 2.3 Frameworks Applied

- PCAOB AS 2201: An Audit of Internal Control Over Financial Reporting
- COSO Internal Control Framework (2013)
- COBIT 5 for Information Security and IT Governance

---

## 3. Control Testing Methodology

### 3.1 Testing Approach

| Testing Method | Used For |
|---------------|---------|
| Inquiry | Understanding of control design and operation |
| Observation | Physical and logical access controls; system configuration |
| Inspection | Review of change tickets, access reviews, backup logs, incident reports |
| Re-performance | Recreating control procedures to verify effectiveness |
| Sampling | Statistical and judgmental sampling of control populations |

### 3.2 Sampling Parameters

| Control Frequency | Minimum Sample Size |
|------------------|---------------------|
| Daily | 25 items |
| Weekly | 15 items |
| Monthly | 12 items (full population) |
| Quarterly | 4 items (full population) |
| Annual | 1 item (full population) |
| Ad hoc (high risk) | Full population |

---

## 4. Detailed Control Results

### 4.1 Logical Access Controls

| Control | Description | Sample | Exceptions | Result |
|---------|-------------|--------|-----------|--------|
| ITGC-LA-01 | User Access Provisioning | 25 of 87 | 0 | Effective |
| ITGC-LA-02 | User Access Termination | 47 of 47 (full) | 0 | Effective |
| ITGC-LA-03 | Quarterly Access Reviews | 4 of 4 (full) | 0 | Effective |
| ITGC-LA-04 | Privileged Access Management | 8 of 8 (full) | 0 | Effective |
| ITGC-LA-05 | Segregation of Duties | All roles reviewed | 0 | Effective |
| ITGC-LA-06 | Password Policy | Configuration + 25 accounts | 0 | Effective |

**Domain Conclusion: All 6 logical access controls are EFFECTIVE. No exceptions noted.**

---

### 4.2 Change Management Controls

| Control | Description | Sample | Exceptions | Result |
|---------|-------------|--------|-----------|--------|
| ITGC-CM-01 | Change Authorization | 40 of 127 | 0 | Effective |
| ITGC-CM-02 | Pre-Implementation Testing | 40 of 127 | 0 | Effective |
| ITGC-CM-03 | Segregation of Duties in Deployment | 25 of 127 | 0 | Effective |
| ITGC-CM-04 | Emergency Change Procedures | 5 of 5 (full) | 0 | Effective |

**Domain Conclusion: All 4 change management controls are EFFECTIVE. No exceptions noted.**

---

### 4.3 Computer Operations Controls

| Control | Description | Sample | Exceptions | Result |
|---------|-------------|--------|-----------|--------|
| ITGC-CO-01 | Job Scheduling and Batch Processing | 12 months of logs | 0 material | Effective |
| ITGC-CO-02 | Backup and Recovery | 730 backups + 4 restore tests | 0 | Effective |
| ITGC-CO-03 | System Availability Monitoring | 12 months of logs | 0 material | Effective |
| ITGC-CO-04 | Incident and Problem Management | 7 of 7 incidents (full) | 1 minor | Effective (with deficiency) |
| ITGC-CO-05 | Physical Security of Infrastructure | AWS SOC 2 + DC log | 0 | Effective |

**Minor Deficiency Detail (ITGC-CO-04):**
- **Finding:** In June 2025, on-call engineer did not escalate a delayed batch job to the CFO within the required 30-minute window
- **Impact:** Job completed successfully; no financial period impacted; no misstatement risk
- **Remediation:** Escalation decision tree updated; team training conducted August 2025
- **Recurrence:** No recurrence in H2 2025
- **Classification:** Minor deficiency — not a significant deficiency or material weakness

**Domain Conclusion: 4 of 5 controls fully effective; 1 control effective with a minor deficiency that was remediated.**

---

### 4.4 Program Development Controls

| Control | Description | Sample | Exceptions | Result |
|---------|-------------|--------|-----------|--------|
| ITGC-PD-01 | Secure SDLC Requirements | 15 projects reviewed | 0 | Effective |
| ITGC-PD-02 | Code Review and Approval | 25 of 98 EHRP releases | 0 | Effective |
| ITGC-PD-03 | SAST/DAST Integration in CI/CD | CI/CD pipeline config | 0 | Effective |

**Domain Conclusion: All 3 program development controls are EFFECTIVE. No exceptions noted.**

---

## 5. Deficiency Classification Framework

| Classification | Definition | FY2025 Count |
|---------------|------------|-------------|
| Control Deficiency | A control does not allow timely detection or prevention of a financial misstatement | 1 (minor, remediated) |
| Significant Deficiency | A deficiency or combination of deficiencies that is less severe than a material weakness | 0 |
| Material Weakness | A deficiency where there is a reasonable possibility that a material misstatement will not be prevented or detected | 0 |

---

## 6. Management Representation

Based on the assessment conducted by the IT Audit Coordinator and reviewed by the CISO, MedCore Health Systems management represents that:

1. IT General Controls over financial reporting were effective throughout the FY2025 assessment period
2. No material weaknesses or significant deficiencies exist as of December 31, 2025
3. The one minor deficiency identified has been remediated and did not recur
4. This assessment was conducted using frameworks consistent with PCAOB AS 2201 and COSO 2013

| Role | Name | Signature | Date |
|------|------|-----------|------|
| IT Audit Coordinator / ISSO | Amara Osei | A. Osei | February 15, 2026 |
| CISO | Jonathan E. Steele | J. Steele | February 15, 2026 |
| CFO | Linda R. Parker | L. Parker | February 15, 2026 |

---

## 7. Coordination with External Auditors

This assessment was provided to Deloitte & Touche LLP in support of their FY2025 financial statement audit. Deloitte performed independent testing of selected ITGCs as part of their audit procedures. Results of external auditor ITGC testing will be reflected in the Management Letter issued in connection with the FY2025 audit opinion.

**Deloitte FY2025 Management Letter Status:** Issued March 10, 2026. No ITGC-related findings included in Management Letter.
