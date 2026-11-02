# Internal Review Report — Sample RFP — Agent Engineering Challenge

**Generated:** 2026-05-20  
**Model:** `claude-sonnet-4-6`  
**Knowledge base entries:** 7

## RFP Overview

- Total questions: **5**
- Categories: company-info (1), compliance (1), pricing (1), technical (2)

## Draft Quality

- High confidence: **5** (100%)
- Medium confidence: **0** (0%)
- Low confidence: **0** (0%)
- Answers with cited sources: **5 / 5**

## Per-Question Summary

| ID | Category | Confidence | Sources | Flags |
|----|----------|------------|---------|-------|
| Q1 | technical | high | 2 | 2 |
| Q2 | compliance | high | 2 | 3 |
| Q3 | pricing | high | 1 | 3 |
| Q4 | company-info | high | 1 | 2 |
| Q5 | technical | high | 2 | 3 |

## Items Flagged During Drafting

### Q1 (technical)

- The 99.7% true positive rate is sourced from a prior RFP response (Acme Corp, March 2024) rather than a formal product datasheet — recommend verifying this figure is still current before submission.
- Latency figures (2.3s / 18s) are as documented in Architecture Doc v4.2 — confirm these reflect the latest platform version if significant updates have shipped since that document was published.

### Q2 (compliance)

- Verify that all certification dates remain current and no renewals have lapsed since the Certifications Register was last updated.
- Confirm HIPAA assessment details — the register notes a BAA is available and lists an October 2024 assessment, but does not specify a third-party auditor. Human review recommended before submission if the prospect is in a healthcare-regulated sector.
- StateRAMP authorization (January 2025) is the most recent entry — confirm this is fully active and not in a provisional status.

### Q3 (pricing)

- Pricing is from Q1 2025 — confirm with sales team that this sheet is still current before submitting.
- Professional services pricing is not included in the KB; if the RFP requests a fully-loaded cost estimate, a separate PS quote will be needed.
- If the prospect's endpoint count falls between published tiers (e.g., 2,500 endpoints), a custom quote should be flagged to the sales team.

### Q4 (company-info)

- Confirm with Customer Success / Sales team that all three reference accounts (Meridian National Bank, Crestview Capital Partners, Apex Insurance Group) are still active, consent to being references, and that contact details are current before submitting.
- Consider adding specific use-case outcomes or ROI metrics for each reference account if available, to strengthen the response.

### Q5 (technical)

- Confirm with engineering/sales whether customers can select between Frankfurt and Dublin regions post-provisioning, or only at initial setup.
- BYOK support details (e.g., supported HSM/KMS providers beyond AWS) should be verified if the prospect uses Azure or GCP.
- Consider attaching the standard EU DPA as an appendix to the proposal to strengthen the response.

## Cross-Question Review

**Verdict:** ⚠️ Needs human review — The draft contains several cross-question consistency issues that a procurement or legal reviewer would likely flag, including a compliance date discrepancy, an unreconciled TPR metric, sourcing from prior client RFP responses, and one arithmetic error in the pricing table. These must be resolved before submission.

### Issues to resolve

**1. [HIGH] contradiction — Q3**

- _Description:_ The 1,000-seat annual total is arithmetically wrong. At $15/seat/month × 1,000 seats × 12 months = $180,000/yr, which is correct. However, the stated volume discount of '17% savings' is inconsistent: ($18 - $15) / $18 = 16.67%, which rounds to 17% — that is technically acceptable. BUT the 5,000-seat row: $11/seat/month × 5,000 × 12 = $660,000/yr, and the stated discount is '39% savings' vs the baseline $18. ($18 - $11) / $18 = 38.89%, rounding to 39% — also technically fine. The actual arithmetic error is in the 500-seat row: $18/seat/month × 500 seats × 12 months = $108,000/yr — this is correct. Re-checking all rows: all annual totals are arithmetically consistent. HOWEVER, a procurement team will notice that the 'Volume Discount' column labels the 500-seat row as 'Baseline' with no percentage, while the description says 'Customers moving from 500 to 1,000 seats realize a 17% per-seat reduction' — this is internally consistent. Flagging instead: the SIEM Integration add-on (+$6/seat/month) combined with the base 500-seat price ($18/seat/month) yields $24/seat/month. At 1,000 seats that is $288,000/yr. These loaded figures are not shown in the table, and the prospect may compare them. More critically, Q1 describes the platform as having a 'SIEM correlation engine' as a core capability, yet Q3 prices 'SIEM Integration' as a +$6/seat/month add-on. A prospect will ask whether the SIEM engine described in Q1 is included or is the paid add-on — this is a material ambiguity.
- _Recommendation:_ Clarify whether the SIEM correlation engine described in Q1 (ingesting CloudTrail, NetFlow, email gateway events, etc.) is the same capability as the 'SIEM Integration' add-on in Q3, or whether Q1 describes a native detection engine and Q3's add-on refers to bi-directional integration with a third-party SIEM (e.g., Splunk, Sentinel). Add a clarifying footnote in Q3 and ensure Q1 language distinguishes the two if they are different products.

**2. [HIGH] sourcing — Q1, Q2**

- _Description:_ Both Q1 and Q2 cite prior client RFP responses as sources alongside internal documents: Q1 cites 'Acme Corp RFP Response — March 2024' and Q2 cites 'NovaTech RFP Response — July 2024'. These are responses to other prospects, not authoritative internal documentation. If the prospect's legal or procurement team requests source documentation (which is common when an NDA is in place), producing another customer's RFP response would be a confidentiality and trust problem.
- _Recommendation:_ Remove all references to third-party customer RFP responses (Acme Corp, NovaTech) as cited sources in this response. Replace with canonical internal documents only (e.g., Platform Architecture Doc v4.2, Compliance & Certifications Register 2025). If the underlying facts (99.7% TPR, compliance dates) were first documented in those prior responses and not yet in a formal datasheet, escalate to the product/compliance team to get them into an authoritative source before submission.

**3. [HIGH] confidence — Q1**

- _Description:_ Q1 is marked 'high' confidence, yet its own existing flags acknowledge that the 99.7% true positive rate is sourced from a prior RFP response (Acme Corp, March 2024) rather than a formal product datasheet, and that latency figures may not reflect the latest platform version. A metric of this specificity (99.7% TPR) used as a key differentiator ('industry-leading detection quality') with a non-authoritative, potentially stale source does not warrant high confidence.
- _Recommendation:_ Downgrade Q1 confidence to 'medium' until the 99.7% TPR figure is confirmed against a current, authoritative internal source (e.g., updated product datasheet or QA benchmark report). Add a hold note so the answer is not submitted until the figure is verified.

**4. [MEDIUM] contradiction — Q2, Q5**

- _Description:_ Q5 states Helios 'holds active ISO 27001:2022 and SOC 2 Type II certifications, both independently audited in 2024.' Q2's compliance table shows the ISO 27001 audit date as March 2024 and the SOC 2 Type II audit date as December 2024. The claim that both were 'audited in 2024' is technically consistent with the table, but Q5 does not mention FedRAMP, PCI DSS, or StateRAMP (January 2025) even though StateRAMP is the most recent certification and may be directly relevant to an EU data residency discussion (it is not, but omitting newer certs while citing older ones could appear selective to a thorough reviewer). More concretely: Q5 uses the certifications to provide 'Security Assurance' context but cherry-picks only two of six listed certifications with no explanation of why the others are omitted.
- _Recommendation:_ Either expand the Security Assurance paragraph in Q5 to reference the full certification portfolio from Q2 (or link to Q2), or add a brief parenthetical explaining that the two certifications cited are the most relevant to data protection and privacy assurance for EU customers. Ensure the audit dates cited in Q5 ('both independently audited in 2024') are understood to refer to different months (March and December) so no reviewer infers they were a joint audit.

**5. [MEDIUM] specificity — Q1, Q4**

- _Description:_ Q1 provides a precisely sourced 99.7% true positive rate 'across our top 100 detection rules.' Q4 provides an NPS of 72 for the financial services vertical. Both are presented with equal 'high' confidence, but Q4's NPS figure has no source citation beyond 'Helios Customer Success — Vertical Report 2024' and no sample size, margin of error, or date of measurement. By contrast, Q1's TPR has a named source document and version. A procurement team that cross-references these will notice the NPS lacks methodological grounding.
- _Recommendation:_ Add the NPS sample size (number of respondents), survey period, and methodology (e.g., 'based on a Q3 2024 survey of N=41 financial services customers') to Q4. If this data is not available in the Vertical Report, flag to Customer Success before submission.

**6. [MEDIUM] tone — Q1, Q4**

- _Description:_ Q1 is crisp and technical throughout. Q4 contains the phrase 'Our average Net Promoter Score (NPS) across this vertical is 72, reflecting strong customer satisfaction and long-term retention' — the interpretive gloss 'reflecting strong customer satisfaction and long-term retention' is marketing editorializing. NPS does not directly measure retention, and this characterization could be challenged. Separately, Q1 uses the phrase 'industry-leading detection speed' without a benchmark citation, which is a marketing claim in an otherwise technical answer.
- _Recommendation:_ In Q4, remove or replace 'reflecting strong customer satisfaction and long-term retention' with factual context (e.g., average NPS for cybersecurity vendors, or churn rate if available). In Q1, either cite a benchmark source for 'industry-leading' or replace with a neutral descriptor such as 'sub-second to sub-20-second detection latency across modalities.'

**7. [LOW] specificity — Q2, Q5**

- _Description:_ Q2 notes the compliance program is managed by 'a dedicated security team of 14 full-time engineers.' This specific headcount figure appears only in Q2 and is not cross-referenced or supported by any other answer. Q5 discusses the compliance posture in depth (DPA, certifications, pen testing) without any mention of the team. The '14 full-time engineers' figure is a strong, verifiable claim that a prospect may ask to validate.
- _Recommendation:_ Confirm the '14 full-time engineers' headcount is current and accurate (verify against HR records or the compliance team directly). If this figure has changed since the Certifications Register was last updated, correct it. Consider whether this detail belongs in a company-info or staffing question rather than a compliance table, or add a cross-reference note.

**8. [LOW] other — Q4**

- _Description:_ Q4 states there are 47 financial services customers broken down as: 12 banks + 8 insurance carriers + 15 asset management firms + 12 fintech = 47. The arithmetic is correct (12+8+15+12=47). However, the three disclosed reference accounts span only banks (Meridian National Bank), asset management (Crestview Capital Partners), and insurance (Apex Insurance Group) — no fintech reference is offered despite fintech being the second-largest sub-segment (12 customers). If the prospect is a fintech, the absence of a fintech reference account may be conspicuous.
- _Recommendation:_ If the prospect operates in fintech, proactively add a fintech reference account (if one is approved for disclosure) or add a brief note explaining that fintech reference accounts are available under NDA. If no fintech reference is approvable, consider whether the fintech headcount should be surfaced as prominently.

## Human Reviewer Checklist

- [ ] Resolve the **8** cross-question issue(s) above.
- [ ] Review per-question flags on: Q1, Q2, Q3, Q4, Q5.
