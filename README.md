# 🛡️ Fraud Detection for E-Commerce and Banking

_A complete end-to-end machine learning solution for financial fraud detection using explainability tools and business insights._

---

## 📌 Overview

Adey Innovations Inc. aims to strengthen fraud detection capabilities for both e-commerce and banking domains. This project builds robust, interpretable machine learning models to identify fraudulent transactions, incorporating SHAP-based explainability and domain-aligned risk recommendations.

---

## 🧠 Problem Statement

Fraudulent transactions not only lead to financial losses but also reduce user trust. The challenge lies in:

- Handling **highly imbalanced datasets**
- **Detecting fraud** without affecting legitimate users
- Ensuring **explainability** for business stakeholders

---

## 📂 Dataset Descriptions

### 1. **E-Commerce Dataset** (`Fraud_Data.csv`)

- Includes user behavior, signup and transaction details, and device metadata.
- Engineered features: `time_since_signup`, `is_weekend`, `device_unique_users`, etc.

### 2. **Credit Card Dataset** (`creditcard.csv`)

- Includes 30 anonymized features (`V1–V28`), transaction time and amount.
- Highly imbalanced: ~0.17% fraud.

---

## ⚙️ Project Structure

```
fraud-detection-adey-2025/
│
├── data/                      # Raw and processed data
├── notebooks/                 # Jupyter Notebooks for EDA, modeling, SHAP
├── outputs/
│   ├── plots/                 # PR Curves, SHAP visualizations
│   └── results/               # CSVs and final insights
├── src/                       # Scripts for modeling, preprocessing
│   ├── preprocessing.py
│   ├── models.py
│   ├── shap_analysis.py
├── final_report/              # Final DOCX & Markdown reports
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## 🧪 Model Training & Evaluation

| Dataset     | Model               | PR AUC     |
| ----------- | ------------------- | ---------- |
| Credit Card | Logistic Regression | 0.7112     |
| Credit Card | Random Forest       | **0.8102** |
| E-Commerce  | Logistic Regression | 0.4076     |
| E-Commerce  | Random Forest       | **0.6226** |

✅ **Random Forest** was chosen as the final model due to superior performance and explainability.

---

## 📊 SHAP Explainability

### Top Global Fraud Predictors:

- `purchase_value`
- `time_since_signup`
- `device_unique_users`
- `is_weekend`
- `is_shared_device`

Visualizations:

- SHAP summary & beeswarm plots
- Force plot for individual cases
- Partial dependence plots (PDPs)
- Waterfall charts

---

## 💼 Key Insights

- Established users are more trustworthy (longer `time_since_signup`)
- Device-sharing and new users raise fraud risk
- High-value and nighttime transactions are strong fraud signals
- SHAP enhances model trust for business use

---

## ✅ Business Recommendations

### 📌 Immediate Actions

- Implement real-time risk scoring
- Deploy alert system for high-value transactions
- Strengthen verification for new users

### 📊 Risk Scoring Formula

```
Risk Score = Base Risk
            - 1.5 * time_since_signup
            - 1.0 * purchase_value
            - 0.7 * age
            - 0.6 * device_unique_users
            - 0.6 * is_weekend
            - 0.5 * is_shared_device
            - 0.5 * hour
            - 0.5 * is_young_user
```

### 📈 Monitoring & Feedback

- Monthly SHAP audits
- A/B test risk thresholds
- Feedback loop integration
- Train analysts on SHAP for case reviews

---

## 🔍 Example SHAP Interpretation

Fraud Case Index 4:

- Model Prediction (LightGBM): 13.6%
- SHAP reveals high fraud risk due to device sharing and night-time behavior.

Non-Fraud Case Index 0:

- Model Prediction (LightGBM): 24.9%
- SHAP confirms lower risk from older age and high `time_since_signup`.

---

## 📦 Installation

```bash
git clone https://github.com/MiskirB/fraud-detection-adey-2025.git
cd fraud-detection-adey-2025
pip install -r requirements.txt
```

---

## 🚀 Running the Project

```bash
# Launch Jupyter for EDA or modeling
jupyter notebook notebooks/EDA_Ecommerce.ipynb
```

---

## 📘 Final Report

The full project write-up is available:

- 📄 [`final_report/Final_Fraud_Detection_Report_with_Insights.docx`](final_report/Final_Fraud_Detection_Report_with_Insights.docx)
- 📄 [`final_report/Final_Fraud_Detection_Report_with_Insights.md`](final_report/Final_Fraud_Detection_Report_with_Insights.md)

---

## 🔗 Author

**Miskir Besir**  
🌐 GitHub: [@MiskirB](https://github.com/MiskirB)  
📬 Email: miskerbab@gmail.com
