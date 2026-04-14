# Algorithmic Fairness & Compliance Audit: Credit Risk Model

### Overview
This project bridges the gap between **Machine Learning** and **Tech Law**. I developed a Random Forest model to predict credit risk using the German Credit Dataset and subsequently audited the model to evaluate its compliance with the **EU AI Act (Article 10)** and the **GDPR (Article 5 - Data Minimization)**.

Unlike standard data science projects that stop at predictive accuracy, this repository provides a comprehensive **algorithmic compliance audit** using statistical hypothesis testing (Chi-Square) and algorithmic fairness metrics, proving that strict legal compliance can be achieved without destroying core business value.

### 🛠️ Tech Stack & Legal Frameworks
* **Language & Libraries:** Python, Pandas, Scikit-learn, Fairlearn, SciPy
* **Legal Frameworks:** EU AI Act (Art. 10 - Data Governance), GDPR (Art. 5(1)(c) - Data Minimization)

---

### TL;DR: Compliance vs. Performance Trade-off
The core objective was to test the "Fairness through Unawareness" approach. By comparing the "Full Model" (containing protected attributes) with the "Blind Model" (stripped of demographics), the audit yielded the following results:

| Metric | Full Model (With Demographics) | Blind Model (GDPR Compliant) | Business & Legal Impact |
| :--- | :--- | :--- | :--- |
| **Accuracy** | 79.50% | 77.50% | -2.00% (Negligible Trade-off) |
| **ROC-AUC** | 0.8013 | **0.8044** | **Increased Risk Generalization!** |
| **F1-Score** | 0.7804 | **0.7629** | Minimal Loss (-0.017) |
| **Legal Status** | High Risk (AI Act Drift) | **Full Compliance (GDPR Art. 5)** | **Regulatory Risk Hedged** |

---

### Key Audit Findings

#### 1. The Fairness Audit (EU AI Act Compliance)
Initial descriptive metrics via `fairlearn` suggested alarming discriminatory patterns (e.g., a 33.3% unfair denial rate for divorced applicants and systemic risk-flagging for youth). 
* However, rigorous **Chi-Square Hypothesis Testing** proved that the system does not exhibit statistically significant bias across Gender, Age, or Marital Status (All P-values > 0.05).
* **Verdict:** The model is cleared of "Disparate Impact" allegations and complies with Article 10 of the EU AI Act.
* **Risk Alert:** Marital Status returned a P-value of 0.0542 (a borderline case), signaling a high risk of "model drift" and requiring strict post-market monitoring under Article 61.

#### 2. The "Blind Model" Experiment (GDPR Compliance)
To test the strict legal necessity of processing sensitive demographic data, I applied the "Fairness through Unawareness" approach. Dropping all protected demographic attributes (Age, Sex, Marital Status) resulted in a negligible 2.00% drop in predictive accuracy.
* **The Engineering Breakthrough:** Crucially, removing these demographic variables actually *improved* the model's underlying risk-ranking capability, increasing the **ROC-AUC score from 0.8013 to 0.8044**. This proves that removing demographic noise enhances model generalization.
* **Verdict:** Processing demographic data is mathematically unnecessary for the core business logic. Retaining these features in the database violates the **GDPR Principle of Data Minimization**.

### Actionable Recommendation
**Implement the Blind Model.** Dropping protected demographic attributes from the feature engineering pipeline ensures absolute GDPR compliance, eliminates the borderline AI Act risk regarding marital status, and preserves 97.5% of the predictive power while actively improving the ROC-AUC score. This strategic adjustment significantly reduces the organization's exposure to regulatory fines without compromising commercial viability.
