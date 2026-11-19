# Project 05: Enterprise Risk Audit & Threat Modeling (NIST CSF / PASTA)

## Executive Summary
This project combines an internal security controls audit with an asset-centric threat modeling assessment to evaluate organizational risk posture. Using the **NIST Cybersecurity Framework (CSF)** and the **PASTA (Process for Attack Simulation and Threat Analysis)** methodology, I audited existing administrative and technical controls (Botium Toys scenario), classified critical business assets, mapped realistic attack vectors, and delivered a prioritized remediation roadmap.

---

## Technical Specifications & Frameworks
* **Governance & Audit Frameworks:** NIST CSF (Identify, Protect, Detect, Respond, Recover), NIST SP 800-53, PCI DSS, GDPR
* **Threat Modeling Methodology:** PASTA (7-Stage Risk-Centric Threat Modeling)
* **Assessment Artifacts:** Controls Audit Checklist, Asset Classification Matrix, Threat & Vulnerability Register
* **Core Focus:** Governance, Risk, and Compliance (GRC), Asset Valuation, Third-Party & Regulatory Risk

---

## Phase 1: Internal Controls Audit (NIST CSF Alignment)

An audit of existing organizational infrastructure revealed critical gaps across access control, data protection, and disaster recovery procedures.

### Key Control Gaps Identified
* **Access & Identity Hygiene:** Lack of formal Role-Based Access Control (RBAC), shared administrative credentials, and no mandatory Multi-Factor Authentication (MFA) for remote or privileged access.
* **Data Protection & Cryptography:** Sensitive customer payment and PII records stored without encryption-at-rest; legacy unencrypted protocols active on internal segments.
* **Resilience & Recovery:** Absence of tested business continuity / disaster recovery (BCDR) plans and irregular off-site backup verification.

---

## Phase 2: Asset Classification & PASTA Threat Modeling

To prioritize remediation based on business impact rather than raw vulnerability count, critical organizational assets were classified and evaluated against threat actor TTPs.

### Asset Valuation & Risk Exposure

| Asset Category | Asset Examples | Classification | Primary Threat Vector | Business Impact |
| :--- | :--- | :--- | :--- | :--- |
| **Customer & Payment Data** | POS Database, E-Commerce PII Records | **Critical / Restricted** | SQL Injection, Credential Stuffing, Unencrypted Exfiltration | Regulatory fines (PCI DSS / GDPR), loss of customer trust |
| **Identity Infrastructure** | Active Directory / IAM Directory | **Critical / Restricted** | Privilege Escalation, Brute Force, Phishing | Full domain compromise and lateral movement |
| **Internal Operations** | Inventory Servers, Point-of-Sale Terminals | **High / Internal** | Ransomware, Unpatched OS Vulnerabilities | Operational downtime and halted order fulfillment |
| **Public Web Presence** | Marketing Website, Public API Endpoints | **Medium / Public** | DDoS, Cross-Site Scripting (XSS), Web Scraping | Brand degradation and service interruption |

---

## Remediation & Governance Roadmap

| Identified Risk | Security Control Recommendation | Framework Alignment | Priority |
| :--- | :--- | :--- | :--- |
| **Missing MFA & Weak IAM** | Enforce phishing-resistant MFA across all accounts; implement RBAC and quarterly access reviews. | **NIST CSF: PR.AC-1 / PR.AC-4** | **P1 (Immediate)** |
| **Unencrypted PII / Cardholder Data** | Implement AES-256 encryption at rest and enforce TLS 1.3 for all data in transit to meet PCI DSS. | **NIST CSF: PR.DS-1 / PR.DS-2** | **P1 (Immediate)** |
| **Unmonitored Network Perimeter** | Deploy centralized SIEM logging, Intrusion Detection Systems (IDS), and automated alerting thresholds. | **NIST CSF: DE.CM-1 / DE.AE-3** | **P2 (Short-Term)** |
| **Untested Recovery Procedures** | Establish automated immutable backups (3-2-1 rule) and conduct semi-annual tabletop BCDR exercises. | **NIST CSF: PR.IP-4 / RC.RP-1** | **P2 (Short-Term)** |

---

## Strategic Takeaways
* **Risk-Based Prioritization:** Pairing a compliance checklist (NIST CSF) with threat modeling (PASTA) prevents security teams from wasting resources on low-impact findings while high-value customer databases remain exposed.
* **Executive Translation:** Framing technical vulnerabilities in terms of regulatory compliance (PCI DSS, GDPR) and operational continuity enables leadership to approve security budgets based on measurable risk reduction.
