# 🏥 Hospital GRC Risk Assessment: Riverside Medical Center

An entry-level **Governance, Risk, and Compliance (GRC)** project: a complete information security risk assessment for a fictional 350-bed hospital, built with **NIST SP 800-30** and mapped to the **HIPAA Security Rule**, **NIST CSF 2.0**, and **HHS 405(d) HICP**.

This project is the assessment behind my earlier project, *Beyond Our Walls*, which proposed a Third-Party Risk Management (TPRM) program after a vendor ransomware incident modeled on the 2024 Change Healthcare attack. That project answered *"what should Riverside do?"* This one answers *"how do we know, and how bad is it?"*

## 📁 What's Inside

| File | What it is |
|---|---|
| [`docs/risk_assessment_report.md`](docs/risk_assessment_report.md) | The full written report: scope, methodology, findings, treatment plan |
| [`Riverside_Risk_Assessment.xlsx`](Riverside_Risk_Assessment.xlsx) | The working risk register (download to open; formulas recalculate as you edit) |
| [`risk_register.csv`](risk_register.csv) | Risk register in CSV format, viewable directly on GitHub |

### The workbook's tabs

- **Start Here:** scoring scales, rating thresholds, and a color legend
- **Asset Register:** eight hospital assets ranked by Criticality × Vulnerability
- **Risk Register:** 15 risks with threat, vulnerability, existing controls, inherent and residual scores, treatment, owner, and framework mapping
- **Heat Map:** auto-updating 5×5 heat maps (before and after treatment)
- **Control Gap Assessment:** 14 safeguards tested against HIPAA, NIST CSF 2.0, and HICP
- **Vendor Tiering:** 13 sample vendors scored and tiered Critical / High / Medium / Low

## 🔎 Key Findings

| Metric | Before treatment | After treatment |
|---|---|---|
| Critical risks | 2 | 0 |
| High risks | 11 | 0 |
| Average risk score (1–25) | 14.3 | 7.3 |

**Top risks:**

| ID | Risk | Score | Rating |
|---|---|---|---|
| R01 | Ransomware via compromised vendor remote access | 25 | 🔴 Critical |
| R02 | Prolonged clearinghouse outage halts revenue and e-prescribing | 20 | 🔴 Critical |
| R03 | Business Associate Agreements lack enforceable security terms | 16 | 🟠 High |
| R05 | Workforce credentials stolen through phishing | 16 | 🟠 High |
| R08 | Former workforce or vendor accounts remain active | 16 | 🟠 High |

**Control gaps:** only 1 of 14 key controls is fully implemented. Vendor tiering, continuous vendor monitoring, and downtime procedures are missing entirely.

**Notable insight:** the HVAC/building automation contractor tiers as a **High-risk vendor despite having zero access to patient data**, because it holds remote access to Riverside's network. Vendor risk is about access, not just PHI.

## 🧭 Methodology

1. **Prepare:** define scope, select frameworks, set 1–5 likelihood and impact scales
2. **Identify:** list assets, threats, and vulnerabilities
3. **Analyze:** score each risk (Likelihood × Impact) with current controls
4. **Evaluate:** test key controls and record gaps
5. **Treat:** recommend controls, assign owners and dates, estimate residual risk
6. **Monitor:** annual reassessment and quarterly governance review

## 📚 Frameworks Used

- **NIST SP 800-30 Rev. 1:** risk assessment process
- **HIPAA Security Rule** (45 CFR §164.308–316): administrative, physical, and technical safeguards
- **NIST CSF 2.0:** Govern, Identify, Protect, Detect, Respond, Recover (including GV.SC, Supply Chain Risk Management)
- **HHS 405(d) HICP:** healthcare-specific cybersecurity practices
- **ASIS ESRM:** asset identification and prioritization (from the companion project)

## 🛠️ Skills Demonstrated

Risk identification and scoring · risk register development · control gap analysis · regulatory mapping (HIPAA) · framework alignment (NIST CSF 2.0) · third-party / vendor risk tiering · risk treatment planning · executive reporting · Excel modeling with formulas and conditional formatting

## 🔗 Related Projects

- [Beyond Our Walls](Beyond_Our_Walls_TPRM_Presentation.pdf): TPRM program proposal for Riverside Medical Center
- [Healthcare Phishing Email Analyzer](https://github.com/TheTolulope/healthcare-phishing-analyzer): Python tool that detects phishing red flags (relates to risk R05)

## ⚠️ Disclaimer

Riverside Medical Center is a fictional organization. The scenario is modeled on public reporting about the February 2024 Change Healthcare ransomware attack. All scores, control statuses, and vendor names are illustrative and created for educational purposes.
