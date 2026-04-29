# Sarbanes-Oxley (SOX) IT General Controls Program

**Organization:** MedCore Health Systems
**Regulation:** Sarbanes-Oxley Act of 2002 — Section 302 and Section 404
**Applicability:** MedCore is privately held but maintains SOX-aligned IT General Controls as a condition of financing agreements and as a best practice for financial reporting integrity
**Framework:** COBIT 5 / PCAOB AS 2201 (IT General Controls)
**External Auditor:** Deloitte & Touche LLP (financial audit engagement)
**Status:** ITGCs Implemented | Annual Internal Assessment Complete
**Last Updated:** April 2026

---

## Overview

While MedCore Health Systems is not a publicly traded company subject to mandatory SOX compliance, the organization maintains Sarbanes-Oxley-aligned IT General Controls (ITGCs) due to:

1. **Lender requirements:** MedCore's primary lender (First National Healthcare Capital) requires SOX-equivalent ITGC attestation as a covenant of its credit facility
2. **Acquisition preparation:** MedCore's strategic plan includes potential acquisition by a publicly traded health system, which would require historical SOX compliance evidence
3. **Best practice:** Mature ITGCs reduce financial reporting risk and demonstrate governance credibility to partners and regulators

---

## IT General Controls in Scope

SOX ITGCs are organized into four control domains that affect financial reporting systems:

| ITGC Domain | Description | In-Scope Systems |
|------------|-------------|-----------------|
| Logical Access | Controls over who can access financial applications | EHR Billing Module, QuickBooks Enterprise, Payroll (ADP) |
| Change Management | Controls over changes to financial applications | Billing application code, QuickBooks configurations |
| Computer Operations | Controls over system availability and operations | Billing servers, EHR billing module, data backups |
| Program Development | SDLC controls for financial application development | Billing module development and maintenance |

---

## Repository Structure

```
sox-it-controls/
├── README.md                              # This file
├── itgc/
│   ├── logical-access-controls.md        # ITGC-LA: Logical access to financial systems
│   ├── change-management-controls.md     # ITGC-CM: Change management for financial apps
│   └── computer-operations-controls.md   # ITGC-CO: Operations and availability
└── assessment/
    └── annual-itgc-assessment.md         # Annual ITGC testing and results
```

---

## Key Personnel

| Role | Name |
|------|------|
| SOX ITGC Program Owner | Jonathan E. Steele, CISO |
| Financial Systems Owner | Linda R. Parker, CFO |
| External Auditor (Financial) | Deloitte & Touche LLP |
| IT Audit Coordinator | Amara Osei, ISSO |

---

## Financial Systems in Scope

| System | Purpose | Relevance to Financial Reporting |
|--------|---------|----------------------------------|
| MedCore EHRP v4.2.1 — Billing Module | Patient billing, claims processing, revenue cycle | Directly impacts revenue recognition |
| QuickBooks Enterprise 2026 | General ledger, AP/AR, financial reporting | Primary financial reporting system |
| ADP Workforce Now | Payroll processing | Material compensation and benefits expense |
| Stripe Payment Platform | Payment card processing | Revenue collection; bank reconciliation |

---

## ITGC Assessment Summary — FY2025

| ITGC Domain | Controls Tested | Effective | Deficiencies | Material Weakness |
|------------|----------------|-----------|-------------|------------------|
| Logical Access | 12 | 12 | 0 | None |
| Change Management | 8 | 8 | 0 | None |
| Computer Operations | 10 | 9 | 1 (minor) | None |
| Program Development | 6 | 6 | 0 | None |
| **Total** | **36** | **35** | **1** | **None** |

**Overall Assessment: ITGCs are EFFECTIVE. No material weaknesses or significant deficiencies identified.**

---

## Framework References

- Sarbanes-Oxley Act of 2002 (15 U.S.C. Section 7262)
- PCAOB Auditing Standard AS 2201 — An Audit of ICFR
- COBIT 5 for Information Security and IT Governance
- COSO Internal Control — Integrated Framework (2013)
- NIST SP 800-53 Rev 5 (complementary technical controls)
