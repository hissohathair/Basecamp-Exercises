# Response to Sample RFP — Agent Engineering Challenge

Prepared by **Helios Security**  
Date: 2026-05-20

---

Thank you for the opportunity to respond to your request for proposal. Below you will find Helios Security's responses to each of your questions, organized by category. Each response is grounded in our current product documentation, certifications register, and commercial pricing sheet.

## Technical

### Q1. Describe your platform's approach to real-time threat detection. What data sources are ingested, and what is the average detection-to-alert latency?

Helios Sentinel employs a multi-layered, real-time threat detection engine that combines three complementary methodologies: (1) signature-based matching for known threat patterns, (2) behavioral analysis for contextual anomaly identification, and (3) ML-driven anomaly detection for novel and emerging threats. Together, these layers enable broad coverage across the MITRE ATT&CK framework, with detection rules validated quarterly.

**Data Sources Ingested:**
The platform ingests a wide range of telemetry streams, including:
- **Endpoint Telemetry:** Process events, file system changes, and network connections from managed endpoints
- **Cloud Workload Logs:** AWS CloudTrail, Azure Activity Log, and GCP Audit Log
- **Network Flow Data:** NetFlow v9 and IPFIX
- **Email Gateway Events:** For phishing, malware delivery, and business email compromise detection

The underlying SIEM correlation engine is capable of processing up to 50,000 events per second (EPS) per tenant, ensuring scalability even in high-volume environments.

**Detection-to-Alert Latency:**
- **Signature-based (known threats):** Average latency of 2.3 seconds
- **Behavioral/ML anomaly detection:** Average latency of 18 seconds

These figures are corroborated by prior RFP responses and our platform architecture documentation. The 99.7% true positive rate on our top 100 detection rules further ensures that alerts are actionable and low-noise.

**References:** Helios Platform Architecture Doc v4.2; Acme Corp RFP Response — March 2024

### Q5. How does your platform handle data residency requirements for customers operating in the EU? Describe encryption at rest and in transit.

Helios Security provides comprehensive support for EU data residency requirements, backed by dedicated regional infrastructure, strong encryption standards, and GDPR-aligned contractual commitments.

**Data Residency**
Helios maintains dedicated cloud infrastructure within the EU across two AWS regions: Frankfurt (eu-central-1) and Dublin (eu-west-1). EU customers can select their preferred region at onboarding, and all customer data — including raw telemetry, alerts, and aggregated analytics — is strictly confined to the chosen region and never transferred outside of it. This architecture ensures compliance with GDPR data localization obligations and applicable Schrems II considerations.

**Encryption at Rest**
All customer data is encrypted at rest using AES-256-GCM, a NIST-approved, authenticated encryption standard. Helios supports customer-managed key (CMK) models via AWS Key Management Service (KMS) or Bring Your Own Key (BYOK), giving customers full control over their encryption keys and the ability to revoke access at any time.

**Encryption in Transit**
All data in transit — including API communications and endpoint agent traffic — is protected using TLS 1.3, the current industry-leading transport security protocol. Endpoint agents additionally enforce certificate pinning, preventing man-in-the-middle attacks and ensuring agents only communicate with verified Helios infrastructure.

**Data Retention**
Data retention policies are configurable on a per-tenant basis. Default retention periods are 90 days for raw telemetry and 13 months for aggregated alerts, supporting both operational needs and regulatory audit requirements.

**GDPR & Contractual Commitments**
A GDPR-compliant Data Processing Agreement (DPA) is included as standard in all EU customer contracts. Additionally, Helios undergoes annual third-party penetration testing conducted by NCC Group, providing independent validation of our security controls.

**References:** Helios Data Sovereignty & Privacy Whitepaper v3.1

---

## Compliance

### Q2. List all compliance certifications your organization currently holds (SOC 2, ISO 27001, FedRAMP, etc.) and the date of most recent audit for each.

Helios Security currently holds the following compliance certifications and authorizations, all actively maintained under a continuous monitoring program with quarterly internal audits:

| Certification | Standard / Level | Most Recent Audit / Authorization Date | Auditing / Certifying Body |
|---|---|---|---|
| SOC 2 Type II | Trust Services Criteria | December 2024 | Deloitte |
| ISO 27001 | ISO/IEC 27001:2022 | March 2024 | BSI |
| FedRAMP | Moderate | June 2024 (Authorization) | DHS (Sponsoring Agency) |
| HIPAA | Business Associate Agreement (BAA) available | October 2024 | Internal Assessment |
| PCI DSS | v4.0, Level 1 Service Provider | September 2024 | Coalfire |
| StateRAMP | Authorized | January 2025 | StateRAMP PMO |

All certifications are maintained on a continuous monitoring basis. Audit reports (e.g., SOC 2 Type II report, FedRAMP package) are available upon request under a mutual NDA. Our dedicated compliance program is managed by a team of 14 full-time security engineers.

**References:** Helios Compliance & Certifications Register 2025; NovaTech RFP Response — July 2024

---

## Pricing

### Q3. Provide per-seat pricing for 500, 1,000, and 5,000 endpoints. Are volume discounts available? Is there a minimum contract term?

Helios Security offers the following per-seat pricing for our Endpoint Protection Platform (EPP+EDR bundle):

**Per-Seat Pricing by Tier:**
| Endpoints | Monthly Per Seat | Annual Total | Volume Discount |
|-----------|-----------------|--------------|------------------|
| 500       | $18/seat/month  | $108,000/yr  | Baseline         |
| 1,000     | $15/seat/month  | $180,000/yr  | 17% discount     |
| 5,000     | $11/seat/month  | $660,000/yr  | 39% discount     |

**Volume Discounts:**
Yes, volume discounts are built into our tiered pricing model, as illustrated above. Customers at 1,000 endpoints receive a 17% reduction versus the baseline rate, and customers at 5,000 endpoints receive a 39% reduction.

**Multi-Year Discounts:**
Additional discounts are available for multi-year commitments:
- 2-year term: additional 5% off
- 3-year term: additional 10% off

**Minimum Contract Term:**
The minimum contract term is 12 months.

**Available Add-Ons (priced per seat/month):**
- SIEM: +$6/seat/month
- Managed Detection & Response (MDR): +$12/seat/month

Note: All pricing above excludes professional services, which are scoped and quoted separately based on deployment requirements.

**References:** Helios Commercial Pricing Sheet Q1 2025

---

## Company Info

### Q4. How many customers do you currently serve in the financial services vertical? Provide 2–3 reference accounts.

Helios Security currently serves 47 customers in the financial services vertical, spanning four sub-segments: 12 banks, 8 insurance carriers, 15 asset management firms, and 12 fintech companies. Our average Net Promoter Score (NPS) across this vertical is 72, reflecting strong customer satisfaction and retention.

Three approved reference accounts are provided below:

1. Meridian National Bank — A regional banking institution with 3,200 endpoints protected under our EPP, EDR, and SIEM suite. Helios has been the primary security platform since 2022.

2. Crestview Capital Partners — An asset management firm with 850 endpoints utilizing our EPP and Managed Detection & Response (MDR) service, deployed since 2023.

3. Apex Insurance Group — One of our longest-tenured financial services customers, with 5,100 endpoints running the full Helios platform since 2021. This deployment represents the breadth and scale of our capabilities in a highly regulated insurance environment.

Helios is pleased to facilitate introductions to any of these reference accounts upon request.

**References:** Helios Customer Success — Vertical Report 2024

---

_Helios Security looks forward to discussing this response with your team._
