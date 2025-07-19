# Interim 1 Report – Fraud Detection for E-Commerce and Banking

**Project**: Adey Innovations Inc.  
**Contributor**: Miskir Besir  
**Submission Date**: July 20, 2025  
**Focus**: Task 1 – Data Cleaning, Feature Engineering, and EDA  
**Repo Link**: https://github.com/MiskirB/fraud-detection-adey-2025

---

## 1. Project Objective

This project aims to improve fraud detection systems in both **e-commerce** and **banking** transaction domains. Using historical transactional data and IP geolocation features, the goal is to build a robust model pipeline that detects fraud while balancing security and user experience. This submission includes exploratory analysis and a detailed preprocessing strategy.

---

## 2. Data Cleaning Summary

### Fraud_Data.csv (E-Commerce)

- Converted `signup_time` and `purchase_time` to datetime objects.
- Removed duplicate records.
- Verified and retained all relevant fields (`browser`, `source`, `device_id`, `age`, etc.).
- Ensured purchase values and ages are positive and numerically consistent.

### IpAddress_to_Country.csv

- Converted lower/upper IP ranges using `ipaddress.IPv4Address` for merging.
- Used `apply()` logic to map each transaction's `ip_address` to a country.

### creditcard.csv (Banking)

- Confirmed data integrity (no nulls, no duplicates).
- Noted anonymized PCA-transformed features (V1–V28).

---

## 3. Feature Engineering

### E-Commerce

- `time_since_signup`: Time delta in seconds between signup and purchase.
- `hour_of_day`: Hour extracted from `purchase_time`.
- `day_of_week`: Day extracted from `purchase_time` (0 = Monday).
- `transaction_count`: Number of purchases by the same `user_id`.
- `country`: Derived from IP address mapping.

---

## 4. Exploratory Data Analysis (EDA)

### Fraud Distribution

- **E-commerce fraud rate**: ~9.36%
- **Credit card fraud rate**: ~0.17%

### Visual Trends:

- **Purchase Value**: Fraud cases often show higher purchase values.
- **Hour of Day**: Fraud spikes during late-night or early-morning hours (1–4 AM).
- **Traffic Source**: Ads show a higher fraud ratio compared to SEO.
- **Browser**: Some browsers (e.g., Opera, Safari) correlated more with fraudulent activity.
- **Geolocation**: Detected country-wise fraud variation using IP mapping.

📁 All plots saved in `outputs/` directory:

- `fraud_distribution.png`
- `purchase_value_by_class.png`
- `fraud_by_hour.png`
- `fraud_by_day.png`
- `fraud_by_source.png`
- `fraud_by_browser.png`
- `fraud_by_country.png`

---

## 5. Class Imbalance Handling Strategy

| Dataset    | Fraud % | Strategy                                       |
| ---------- | ------- | ---------------------------------------------- |
| E-commerce | ~9%     | SMOTE oversampling on training split           |
| Banking    | ~0.17%  | SMOTE or combined sampling (e.g., SMOTE+Tomek) |

- Resampling will be performed **only on the training set** to prevent leakage.
- Evaluation will rely on **AUC-PR**, **F1-score**, and **confusion matrix** due to the high imbalance.

---

## 6. Next Steps

- Implement classification models: Logistic Regression and XGBoost or Random Forest.
- Perform stratified train-test split.
- Compare model performance with class-sensitive metrics.
- Apply SHAP for model interpretability in Task 3.

---

**End of Interim 1 Report**
