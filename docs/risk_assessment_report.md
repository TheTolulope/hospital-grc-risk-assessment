# Information Security Risk Assessment: Riverside Medical Center

**Assessment period:** September 2026
**Prepared by:** Tolu Adelaja
**Methodology:** NIST SP 800-30 Rev. 1, *Guide for Conducting Risk Assessments*
**Control frameworks:** HIPAA Security Rule (45 CFR Part 164, Subpart C), NIST Cybersecurity Framework (CSF) 2.0, HHS 405(d) Health Industry Cybersecurity Practices (HICP)

> Riverside Medical Center is a fictional organization created for a portfolio project. Scenario details are modeled on public reporting about the February 2024 Change Healthcare ransomware attack. Control statuses and evidence notes are illustrative.

---

## 1. Executive Summary

Riverside Medical Center (350 beds, 2,400 employees, 1,300+ vendor relationships) experienced a three-week outage in Q1 2026 when its claims clearinghouse was hit by ransomware through a vendor remote-access account without multi-factor authentication. Riverside's own network was not breached, but claims, prior authorizations, and e-prescribing all stopped.

This assessment evaluated 15 information security risks across Riverside's prioritized assets and tested 14 key safeguards against HIPAA and NIST CSF 2.0.

**Key results:**

- **2 Critical and 11 High risks** at current (inherent) levels. Both Critical risks involve third-party vendors: ransomware through vendor remote access (R01, score 25) and a prolonged clearinghouse outage (R02, score 20).
- **Only 1 of 14 key controls is fully implemented.** Ten are partial and three are missing entirely: vendor tiering, continuous vendor monitoring, and downtime procedures.
- **Vendor risk is the dominant theme.** Six of the 13 High-or-Critical risks stem from third parties or vendor access.
- **Full treatment would bring all 15 risks to Medium or Low** and cut the average risk score by about half (from 14.3 to 7.3).

**Recommendation:** Approve the five-pillar Third-Party Risk Management (TPRM) program proposed in *Beyond Our Walls* ($430,450 over 18 months), and fund four supporting internal controls: MFA everywhere, immutable backups, automated deprovisioning, and documented downtime procedures.

---

## 2. Scope and Objectives

**In scope:** information systems and processes supporting Riverside's claims, billing, and clinical data (EHR, revenue cycle, e-prescribing); medical devices maintained by vendors; workforce and vendor access; and the physical and environmental conditions affecting those systems. Two non-cyber assets (controlled substances and radioactive materials) are included at a summary level to show enterprise coverage.

**Out of scope:** clinical quality and patient safety risks unrelated to information security, financial investment risk, and detailed physical security testing.

**Objectives:**
1. Identify and score risks to Riverside's highest-priority assets.
2. Measure current controls against HIPAA Security Rule requirements and NIST CSF 2.0.
3. Tier a representative sample of vendors to show how oversight should be prioritized.
4. Recommend risk treatments and show expected residual risk.

---

## 3. Methodology

The assessment follows the four steps of NIST SP 800-30 Rev. 1: **prepare** (scope, frameworks, scales), **conduct** (identify threats and vulnerabilities, score likelihood and impact), **communicate** (this report and the risk register), and **maintain** (annual reassessment by the Vendor Risk Governance Subcommittee).

**Scoring.** Each risk is rated on a 1–5 Likelihood scale and a 1–5 Impact scale. Risk Score = Likelihood × Impact (1–25).

| Score | Rating | Required response |
|---|---|---|
| 20–25 | Critical | Treat immediately; executive owner; report to board |
| 12–19 | High | Treatment plan within 30 days |
| 6–11 | Medium | Treat within 12 months or formally accept |
| 1–5 | Low | Monitor; may be accepted by risk owner |

**Inherent vs. residual.** *Inherent* risk reflects current controls only. *Residual* risk is the expected level after the recommended controls are fully in place.

Full scale definitions are in the workbook's *Start Here* tab.

---

## 4. Asset Prioritization

Assets and scores come from ESRM Steps 1–2 in *Beyond Our Walls*. Priority Score = Criticality × Vulnerability (each 1–10).

| Rank | Asset | Criticality | Vulnerability | Priority Score |
|---|---|---|---|---|
| 1 | Claims, Billing & Clinical Data Systems | 9 | 9 | 81 |
| 2 | Controlled-Substance Inventory | 9 | 6 | 54 |
| 3 | Medical Device & IoT Fleet | 7 | 6 | 42 |
| 4 | Physical Campus & Infrastructure | 8 | 4 | 32 |
| 5 | Brand Reputation & Patient Trust | 6 | 5 | 30 |
| 6 | Blood Bank & Biologics | 7 | 4 | 28 |
| 7 | Radioactive Materials | 8 | 3 | 24 |
| 8 | Workforce & Key Personnel | 7 | 3 | 21 |

Because the claims, billing, and clinical data asset scored highest by a wide margin, 11 of the 15 risks in the register focus on it.

---

## 5. Risk Findings

### 5.1 Summary

| ID | Risk | Inherent | Rating | Residual | Rating |
|---|---|---|---|---|---|
| R01 | Ransomware via compromised vendor remote access | 25 | Critical | 10 | Medium |
| R02 | Prolonged clearinghouse outage halts revenue and e-prescribing | 20 | Critical | 9 | Medium |
| R03 | BAAs lack enforceable security terms | 16 | High | 8 | Medium |
| R05 | Workforce credentials stolen through phishing | 16 | High | 8 | Medium |
| R08 | Former workforce or vendor accounts remain active | 16 | High | 6 | Medium |
| R06 | Ransomware spreads through unpatched internal systems | 15 | High | 10 | Medium |
| R07 | EHR data cannot be restored after a destructive attack | 15 | High | 8 | Medium |
| R10 | Medical devices compromised through vendor maintenance connections | 15 | High | 8 | Medium |
| R12 | Hurricane or extended power loss disrupts campus and data center | 15 | High | 9 | Medium |
| R04 | Compromise of a vendor's subcontractor (fourth party) | 12 | High | 8 | Medium |
| R09 | Inappropriate employee access to patient records | 12 | High | 6 | Medium |
| R11 | Controlled-substance diversion from dispensing cabinets | 12 | High | 6 | Medium |
| R13 | Third-party incident not covered by IR plan | 12 | High | 6 | Medium |
| R14 | Lost or stolen laptop exposes PHI | 9 | Medium | 2 | Low |
| R15 | Theft or loss of radioactive sealed sources | 5 | Low | 5 | Low |

### 5.2 Critical Findings

**R01: Ransomware via compromised vendor remote access (25, Critical).**
Vendor remote-access accounts are not required to use MFA, and Riverside never verifies this at onboarding. This is the exact entry point used in the Change Healthcare attack, so likelihood is rated 5 (actively exploited in healthcare now). Impact is 5 because a compromise could reach claims, billing, and clinical data at once.
*Treatment:* phishing-resistant MFA for all vendor access, brokered or just-in-time vendor sessions, and continuous monitoring of Critical-tier vendors. Residual impact stays at 5 because the asset is still critical; the reduction comes from lowering likelihood.

**R02: Prolonged clearinghouse outage (20, Critical).**
Riverside depends on one clearinghouse with no failover and no manual downtime procedures, so the Q1 2026 incident became a cash-flow and patient-care event.
*Treatment:* pre-contract a secondary clearinghouse, document and drill manual procedures for claims and e-prescribing, and maintain a cash-reserve plan. This is the only risk where residual *impact* drops significantly (5 to 3), because resilience limits the damage even if the vendor fails again.

### 5.3 Notable High Findings

- **R05 (Phishing) and R08 (Stale accounts):** both are credential problems. Combined with R01, they show that identity is Riverside's weakest control area.
- **R07 (Backups):** backups exist, but none are immutable and a full restore has never been tested. An untested backup should be treated as a hope, not a control.
- **R10 (Medical devices):** device vendors hold always-on remote access to devices on shared networks. This is a third-party risk *and* a patient safety risk.
- **R12 (Hurricane):** a single on-site data center on the Gulf Coast is a significant availability risk regardless of cyber controls.

---

## 6. Control Gap Assessment

Fourteen key safeguards were tested. Full details and evidence notes are in the workbook's *Control Gap Assessment* tab.

| Status | Count | Share |
|---|---|---|
| Implemented | 1 | 7% |
| Partial | 10 | 71% |
| Not Implemented | 3 | 21% |

**Not implemented:** vendor inventory and tiering (C02), continuous vendor monitoring (C04), and contingency/downtime procedures (C08). The first two are the foundation of the TPRM program; the third is the root cause of R02's severity.

**Most consequential partial controls:**
- **MFA (C01):** enforced for employee VPN only; vendor portals and webmail are exempt.
- **Access deprovisioning (C09):** a sample review found 47 active accounts belonging to departed staff.
- **Patch management (C06):** median 63 days to remediate critical vulnerabilities.

---

## 7. Third-Party Risk: Vendor Tiering Results

Thirteen representative vendors were scored 0–3 on PHI access, system integration, operational criticality, and remote access. Clearinghouse and EHR vendors are Critical by default.

| Tier | Count | Vendors |
|---|---|---|
| Critical | 4 | Claims clearinghouse, EHR platform, revenue cycle outsourcer, dispensing cabinet vendor |
| High | 4 | Imaging/PACS, infusion pump manufacturer, cloud backup, building automation contractor |
| Medium | 2 | Medical transcription, collections agency |
| Low | 3 | Staffing agency, linen service, food service |

**Key insight:** the building automation (HVAC) contractor tiers as **High** despite having **no PHI access**, because it holds remote access to systems on Riverside's network. A PHI-only view of vendor risk would miss this, which is why the tiering model scores remote access and integration separately.

Extrapolated across 1,300+ vendors, this distribution shows why tiering matters: intensive oversight can be concentrated on the small share of vendors that could actually cause a Critical event.

---

## 8. Risk Treatment Plan

Treatments are aligned to the three TPRM program phases.

| Phase | Timing | Treatments | Risks addressed |
|---|---|---|---|
| Phase 1: Foundation | Aug–Nov 2026 | Vendor inventory and tiering; BAA modernization; MFA for remote and email access; automated deprovisioning; laptop encryption enforcement; downtime procedures and secondary clearinghouse | R02, R03, R05, R08, R14 |
| Phase 2: Technology & Governance | Dec 2026–May 2027 | Continuous vendor monitoring; brokered vendor access; fourth-party disclosure; third-party IR playbook and tabletop; immutable backups and restore testing; patching SLA and EDR; EHR access monitoring; ADC diversion analytics | R01, R04, R06, R07, R09, R11, R13 |
| Phase 3: Expansion & Optimization | Jun 2027–Jan 2028 | Medical device segmentation and inventory; secondary hosting/cloud failover; monitoring extended to Medium-tier vendors | R10, R12 |

**Risk acceptance:** R15 (radioactive sources) is accepted at Low. Existing NRC-required controls are appropriate and further investment is not justified by this assessment. The Radiation Safety Officer is the accepting owner, with annual review.

---

## 9. Residual Risk

If all recommended treatments are completed:

- Critical risks: **2 → 0**
- High risks: **11 → 0**
- Average risk score: **14.3 → 7.3** (about 49% reduction)

Thirteen risks remain at Medium. This is expected for a hospital: impact stays high because the assets are inherently critical, so the remaining risk must be managed through monitoring rather than eliminated. These Medium risks will be tracked quarterly by the Vendor Risk Governance Subcommittee.

---

## 10. Limitations

- Riverside is fictional, and likelihood and impact scores reflect analyst judgment informed by public incident data rather than internal loss history.
- The vendor sample (13 of 1,300+) is illustrative, not statistically representative.
- No technical testing (vulnerability scanning or penetration testing) was performed. Control statuses reflect the illustrative scenario.
- A qualitative 5×5 model is simple and widely used, but it doesn't express risk in dollars. A future iteration could apply a quantitative method such as FAIR to the two Critical risks.

---

## 11. References

- American Hospital Association. (2024). *Survey findings on hospital impact of the Change Healthcare cyberattack.*
- Allen, B. J., & Loyear, R. (2017). *Enterprise Security Risk Management: Concepts and Applications.* Rothstein Publishing.
- National Institute of Standards and Technology. (2012). *Guide for Conducting Risk Assessments* (NIST SP 800-30 Rev. 1).
- National Institute of Standards and Technology. (2022). *Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations* (NIST SP 800-161 Rev. 1).
- National Institute of Standards and Technology. (2024). *The NIST Cybersecurity Framework (CSF) 2.0.*
- U.S. Department of Health and Human Services. *HIPAA Security Rule,* 45 CFR Part 164, Subpart C.
- U.S. Department of Health and Human Services, 405(d) Program. (2023). *Health Industry Cybersecurity Practices: Managing Threats and Protecting Patients.*
