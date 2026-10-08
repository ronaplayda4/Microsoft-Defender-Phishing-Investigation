
# Microsoft Defender XDR | Phishing Email Investigation

**SOC Analyst Portfolio Project | Microsoft Defender for Office 365 | October 2026**

## Project Overview

This project documents a hands-on Security Operations Center (SOC) investigation of an authorized phishing simulation conducted in a Microsoft 365 lab environment.

The objective was to evaluate Microsoft Defender's ability to detect, classify, and contain a phishing email impersonating Microsoft 365 IT support.

The investigation included email header analysis, URL reputation checks, threat classification, quarantine verification, and recipient activity review.

**Final Outcome: Phishing successfully detected, blocked, and quarantined. No URL clicks observed.**

## Tools and Technologies

- Microsoft Defender XDR
- Microsoft Defender for Office 365
- Microsoft Defender Threat Explorer
- Microsoft Message Header Analyzer
- Microsoft Sentinel
- Microsoft Entra ID
- VirusTotal
- Kusto Query Language (KQL)

## 1. Investigation Summary

| Field | Details |
|---|---|
| Investigation Type | Authorized phishing simulation |
| Detection | High-confidence phishing |
| Severity | High |
| Email Subject | Action Required: Microsoft 365 Account Verification |
| Sender | External Outlook.com test account |
| Recipient | Microsoft 365 lab user |
| Delivery Action | Blocked |
| Final Location | Quarantine |
| URL Clicks | None observed |
| MITRE ATT&CK | T1566.002 — Spearphishing Link |
| Final Verdict | Informational, Expected Activity — Security Testing |

## 2. Phishing Email Analysis

The simulated phishing email impersonated an IT support team and requested urgent Microsoft 365 account verification.

### Suspicious Indicators

- Urgent verification request within 24 hours
- Threat of temporary account restrictions
- IT support impersonation
- Account verification link
- Social engineering designed to pressure the recipient

The email contained a phishing simulation disclaimer and used a reserved example domain rather than a credential-harvesting website.

## 3. Email Authentication and Header Analysis

Email headers were examined to determine sender authentication status and Microsoft filtering decisions.

| Security Check | Result |
|---|---|
| SPF | Pass |
| DKIM | Pass |
| DMARC | Pass |
| Composite Authentication | Pass |
| ARC | Pass at receiving hop |
| Spam Confidence Level | 8 |
| Protection Policy Category | HPHISH |
| Spam Filtering Verdict | SPM |
| Bulk Complaint Level | 0 |

### Analyst Finding

Although the email passed SPF, DKIM, and DMARC authentication, Microsoft Defender classified it as high-confidence phishing.

This demonstrates that successful email authentication does not guarantee that a message is safe.

## 4. URL Reputation Investigation

**Test URL:** `https://example.com/security-verification`

The URL was investigated using VirusTotal.

### Findings

- No malicious reputation detections were reported.
- The domain was reserved for example and testing purposes.
- No URL clicks were observed in the available telemetry.
- No evidence of credential submission was identified.

A clean URL reputation result does not eliminate phishing risk.

## 5. Microsoft Defender Detection and Response

Microsoft Defender detected the suspicious email using advanced filtering and impersonation detection.

### Observed Response

1. The email was received for security evaluation.
2. Microsoft Defender identified phishing characteristics.
3. The message was classified as high-confidence phishing.
4. Normal inbox delivery was blocked.
5. The email was placed in quarantine.

The quarantine action successfully contained the simulated threat.

## 6. Identity and Sign-In Activity Review

The recipient's identity timeline was reviewed using Microsoft Defender and Microsoft Sentinel.

The timeline contained successful and failed authentication events, Microsoft Graph activity, and Conditional Access blocks.

These identity events were not confirmed to be caused by the simulated phishing email and were treated as separate investigation findings.

No successful sign-in attributable to the phishing email was identified.

## 7. Impact Assessment

| Investigation Question | Result |
|---|---|
| Was the email detected? | Yes |
| Was normal inbox delivery blocked? | Yes |
| Was the email quarantined? | Yes |
| Were URL clicks observed? | No |
| Was credential theft identified? | No evidence |
| Was account compromise established? | No |
| Was additional email containment necessary? | No |

## 8. Final SOC Analyst Verdict

**Classification:** Informational, Expected Activity

**Determination:** Security Testing

**Status:** Investigation Completed

The investigation confirmed that Microsoft Defender successfully detected and quarantined the authorized phishing simulation.

No URL clicks were observed, and no evidence connected the phishing email to account compromise.

The case was documented as a successful security-control validation exercise.

## 9. Lessons Learned

This investigation reinforced several important SOC analyst principles:

- SPF, DKIM, and DMARC authentication do not guarantee email safety.
- Email content and impersonation indicators must be evaluated independently.
- URL reputation alone is insufficient to determine phishing risk.
- Quarantine status and recipient interaction are essential investigation evidence.
- Identity alerts should not be attributed to phishing without supporting correlation.
- Accurate documentation and classification are important parts of incident response.

## 10. Evidence and Documentation

The portfolio evidence includes:

- Phishing email preview
- Microsoft Defender detection details
- Email header analysis
- URL reputation investigation
- Quarantine and delivery status
- Recipient activity investigation
- Redacted identity and Sentinel timelines
- Final SOC investigation report

All evidence should be reviewed and sanitized before public publication. IP addresses, account identifiers, tenant details, and other sensitive information should be concealed.

## Ethical and Authorized Testing

This project was conducted in an authorized Microsoft 365 security lab for educational and defensive cybersecurity training purposes.

No real-world credential harvesting was performed. The simulation used a reserved example domain.

---

**Project Focus:** SOC Analysis | Phishing Investigation | Microsoft Defender XDR | Email Security | Incident Response
