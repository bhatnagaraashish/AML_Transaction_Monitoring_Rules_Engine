## **🛡️AML Transaction Monitoring – Rules-Based Risk Scoring Engine** 

**📌 Project Overview**  
Financial institutions are required under global and local regulations (FATF, EU AML Directives, and Central Bank of Ireland expectations) to identify, monitor, and report suspicious customer activity in a timely and risk-based manner.
This project simulates an end-to-end AML transaction monitoring framework using synthetic but realistic data. It demonstrates how customer risk profiles, transaction behaviour, and rule-based monitoring logic combine to generate explainable alerts suitable for analyst review and compliance reporting.
The emphasis is on risk-based monitoring, transparency, and auditability, rather than purely technical implementation.

## **🎯 Business & Regulatory Rationale**
Transaction monitoring systems must:
Operate on a risk-based approach
Detect both obvious and non-obvious suspicious behaviour (e.g. structuring)
Prioritise alerts based on customer and transaction risk
Provide clear rationale for every alert raised

This project mirrors how first-line AML monitoring functions operate within banks, fintechs, and crypto platforms.

## **🧱 Project Architecture**

## **AML_Transaction_Monitoring_Rules_Engine/**
├── data/ │ ├── customers.csv ├── transactions.csv

├── notebooks/├── 01_data_generation.ipynb ── 02_transaction_monitoring_rules.ipynb ── 03_risk_scoring_and_alerts.ipynb

├── outputs/ ── alerts.csv ── risk_summary.csv

├── README.md

└── LICENSE

## **📊 Dataset Design & Rationale**
Customer Dataset (customers.csv)
| Attribute       | Rationale                                                    |
| --------------- | ------------------------------------------------------------ |
| customer_type   | Monitoring expectations differ for individuals vs businesses |
| country         | Jurisdictional risk is a core AML risk driver                |
| risk_rating     | Enables proportional, risk-based monitoring                  |
| pep_flag        | PEPs require enhanced due diligence                          |
| onboarding_date | Supports lifecycle and review considerations                 |

Risk distributions are designed to reflect real AML portfolios, with a majority of low-to-medium risk customers and a smaller high-risk and PEP population.

## **Transaction Dataset (transactions.csv)**

| Attribute        | Rationale                                    |
| ---------------- | -------------------------------------------- |
| amount           | Core trigger for threshold-based rules       |
| transaction_date | Enables velocity and structuring analysis    |
| channel          | Cash and crypto carry higher inherent risk   |
| country          | Captures cross-border and high-risk exposure |
| transaction_type | Credit and debit risks differ                |

A small proportion of near-threshold transactions are intentionally introduced to simulate structuring and threshold-avoidance behaviour.

## **🧠 Monitoring Rules & Rationale**

| Rule                       | AML Rationale                                 |
| -------------------------- | --------------------------------------------- |
| High-value transactions    | Identifies unusually large movements          |
| High-risk country exposure | Aligns with FATF jurisdictional risk guidance |
| Velocity / structuring     | Detects threshold-avoidance behaviour         |
| PEP enhanced monitoring    | Required under EDD obligations                |

Each rule generates an independent flag, ensuring explainability and audit readiness.

## **⚖️ Risk Scoring Framework**

Instead of relying on single rule breaches, alerts are prioritised using risk-weighted scoring.

| Risk Factor        | Score |
| ------------------ | ----- |
| High-risk customer | +30   |
| PEP                | +40   |
| High-risk country  | +20   |
| Velocity breach    | +25   |

**Alert Classification**

Low Risk: < 30
Medium Risk: 30–60
High Risk: > 60

This approach mirrors how AML teams prioritise analyst workload in production environments.

## **📈 Outputs & Compliance MI**
**Key Outputs**

**alerts.csv** – analyst-ready alert queue

**risk_summary.csv** – management information view

**Example Insights**

* Alert distribution by risk level
* Most frequently triggered rules
* Concentration of alerts among high-risk customers

## **🔍 Key Findings**
* Risk-based scoring improves prioritisation over single-rule alerts
* High-risk customers and PEPs generate a disproportionate share of high-risk alerts
* Structuring behaviour becomes visible only when transaction timing and values are analysed together
* Rule-level transparency supports regulatory explainability and QA review

## **⚠️ Assumptions & Limitations**
* All data is synthetic and for demonstration purposes only
* Sanctions screening and adverse media are out of scope
* FX conversion and typology-specific SAR logic are not implemented
* Alerts assume human analyst review

## **🚀 How to Run**
1. Run the notebooks in the following order:
* 01_data_generation.ipynb
* 02_transaction_monitoring_rules.ipynb
* 03_risk_scoring_and_alerts.ipynb

Install dependencies if required: pip install pandas numpy matplotlib

## **📝 Why This Project Matters**
This project demonstrates the ability to:
* Translate regulatory expectations into technical logic
* Apply risk-based AML principles in practice
* Design explainable and auditable monitoring frameworks
* Bridge compliance, data analysis, and QA thinking
Relevant for roles in AML, Transaction Monitoring, Compliance, QA, and FinTech Risk.

## **🔖 License**
This project is released under the MIT License.
