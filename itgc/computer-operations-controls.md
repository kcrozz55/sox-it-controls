# SOX ITGC — Computer Operations Controls (ITGC-CO)

**Document ID:** SOX-CO-001
**Version:** 1.0
**Classification:** Internal
**Owner:** Thomas J. Bridwell, Systems Administrator
**Approved By:** Linda R. Parker, CFO
**Effective Date:** January 1, 2026
**Assessment Period:** January 1, 2025 – December 31, 2025

---

## Purpose

Computer Operations IT General Controls ensure that the financial reporting systems operate reliably, that data processed by those systems is accurate and complete, and that backup and recovery capabilities protect against loss of financial data.

---

## Control ITGC-CO-01: Job Scheduling and Batch Processing

**Control Objective:** Automated batch jobs that affect financial reporting (billing runs, revenue recognition, payroll processing) execute completely, on schedule, and in the correct sequence.

**Control Description:** All batch jobs are scheduled via AWS EventBridge and monitored by the operations team. Job failure alerts are sent to the IT Security on-call team and the billing supervisor. Failed jobs are investigated and rerun within the same business day.

**Control Owner:** Thomas J. Bridwell, Systems Administrator

**Key Batch Jobs in Scope:**
| Job | Schedule | System | Failure Alert |
|-----|---------|--------|--------------|
| Nightly billing charge posting | 11:00 PM EST daily | EHRP Billing Module | PagerDuty alert to on-call + billing supervisor |
| Daily claims submission to payers | 2:00 AM EST daily | EHRP / EDI gateway | PagerDuty alert + CFO notification if > 4 hrs delayed |
| Monthly revenue recognition close | Last business day, 6:00 PM | EHRP / QuickBooks | CFO notification required |
| Bi-weekly payroll processing | Friday 10:00 AM | ADP Workforce Now | HR Director + CFO notification |

**Testing Evidence (FY2025):**
- Population: 3,650 scheduled batch job executions across all financial batch jobs (FY2025)
- Sample: Job completion logs for all 12 months reviewed
- Results: 3,647/3,650 jobs completed successfully on schedule
- 3 job failures in FY2025: all 3 investigated and rerun within 4 hours; root causes documented and resolved
- 0 failures affected financial statement closing or payroll delivery
- **Control Result: EFFECTIVE — No exceptions noted** (3 failures were detected, investigated, and remediated as designed)

---

## Control ITGC-CO-02: Backup and Recovery of Financial Data

**Control Objective:** Financial system data is backed up regularly and can be restored to support recovery within defined RTO and RPO targets.

**Control Description:** Financial system data is backed up daily using automated AWS RDS snapshots and S3 lifecycle policies. Backup completion is monitored via CloudWatch; failures trigger immediate alerts. Restore capability is tested quarterly.

**Control Owner:** Thomas J. Bridwell, Systems Administrator

**Backup Configuration:**
| System | Backup Method | Frequency | Retention | Cross-Region? |
|--------|--------------|-----------|-----------|--------------|
| EHRP Billing Database (RDS PostgreSQL) | AWS RDS automated snapshot | Daily | 35 days | Yes (us-gov-west-1) |
| QuickBooks Enterprise data files | Nightly file backup to S3 | Daily | 90 days | Yes |
| ADP data | ADP-managed (vendor SLA) | Real-time | Per ADP SLA | ADP-managed |

**Backup SLA:** RTO = 4 hours; RPO = 24 hours (daily backup cadence)

**Testing Evidence (FY2025):**
- Population: 365 daily backup executions for EHRP Billing Database + 365 for QuickBooks
- All daily backup completion logs reviewed
- Results: 730/730 backups completed successfully; 0 backup failures in FY2025
- Quarterly restore tests: 4 tests conducted (March, June, September, December 2025)
- All 4 restore tests successful; restore times ranged from 1h 55m to 3h 47m (all within 4-hour RTO)
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-CO-03: System Availability Monitoring

**Control Objective:** Financial systems are monitored for availability and performance; outages are detected promptly and escalated appropriately.

**Control Description:** AWS CloudWatch monitors all financial system components. Availability threshold alerts (system unavailable > 2 minutes) are sent to PagerDuty and escalated to the on-call engineer. CFO is notified of any outage affecting financial processing that exceeds 30 minutes.

**Control Owner:** Keisha M. Robertson, Cloud Security Engineer

**Testing Evidence (FY2025):**
- 12 months of CloudWatch alert logs reviewed
- EHRP Billing Module uptime: 99.97% (1 outage, 43 minutes, August 2025 — patching overrun)
- August outage: CFO notified within 32 minutes; billing operations resumed before end of business day; no financial period impacted
- QuickBooks: 100% availability; no unplanned outages
- ADP: Per vendor SLA report — 99.98% uptime
- **Control Result: EFFECTIVE — 1 incident was detected, escalated, and resolved as designed**

---

## Control ITGC-CO-04: Incident and Problem Management for Financial Systems

**Control Objective:** Incidents affecting financial reporting systems are logged, investigated, and resolved in a timely manner with appropriate documentation.

**Control Description:** All incidents affecting financial systems are logged in ServiceNow. Priority 1 incidents (complete financial system outage) require CISO and CFO notification within 30 minutes. Root cause analyses are completed within 5 business days for P1 incidents.

**Control Owner:** Amara Osei, ISSO

**Testing Evidence (FY2025):**
- Population: 7 incidents involving financial systems in FY2025
- All 7 reviewed (full population)
- Results: 7/7 incidents logged in ServiceNow; 7/7 had assigned owners; 1 P1 incident (August outage) had CFO notified within 32 minutes and RCA completed within 3 business days
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Control ITGC-CO-05: Physical Security of Financial System Infrastructure

**Control Objective:** Physical access to servers hosting financial systems is restricted to authorized personnel.

**Control Description:** Financial system infrastructure is hosted in AWS GovCloud (logical physical security managed by AWS) and on-premises in the Atlanta Data Center (physical access restricted via biometric + badge access). AWS SOC 2 Type II report provides annual assurance over physical security controls.

**Control Owner:** Jonathan E. Steele, CISO

**Testing Evidence (FY2025):**
- AWS SOC 2 Type II report reviewed (FY2025, issued November 2025): No exceptions to physical security controls
- Atlanta Data Center badge access log reviewed: 0 unauthorized access attempts
- **Control Result: EFFECTIVE — No exceptions noted**

---

## Computer Operations Summary — FY2025

| Control ID | Control Name | Result | Exceptions |
|------------|-------------|--------|-----------|
| ITGC-CO-01 | Job Scheduling and Batch Processing | Effective | 0 (3 failures detected and remediated per design) |
| ITGC-CO-02 | Backup and Recovery | Effective | 0 |
| ITGC-CO-03 | System Availability Monitoring | Effective | 0 (1 incident detected and resolved per design) |
| ITGC-CO-04 | Incident and Problem Management | Effective | 0 |
| ITGC-CO-05 | Physical Security of Infrastructure | Effective | 0 |
| **Overall** | | **Effective** | **0 material exceptions** |

---

## Note on Minor Deficiency (Reported in Annual Assessment)

During Q2 2025, one monthly billing batch job (EHRP monthly revenue recognition close — June 30, 2025) completed 2 hours and 15 minutes late due to an unanticipated database performance issue. While the batch job completed successfully and the monthly close was not affected (completed before EOD), the incident was not escalated to the CFO within the required 30-minute window because the on-call engineer assessed it as a monitoring alert rather than an escalatable incident.

**Assessment:** Minor deficiency — detection and remediation controls functioned, but escalation procedure was not followed for a potentially CFO-relevant event.
**Remediation:** On-call escalation decision tree updated; training conducted with operations team (August 2025); no recurrence in H2 2025.
**Auditor Assessment:** This deficiency is not considered a significant deficiency or material weakness. Controls were otherwise effective throughout FY2025.
