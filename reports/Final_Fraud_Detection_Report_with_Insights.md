---
title: Fraud Detection for E-Commerce and Banking
---

# Overview

Adey Innovations Inc. is a fintech company tackling fraud detection in
both e-commerce and banking environments. The objective of this project
was to create accurate, interpretable fraud detection models and
communicate insights using explainability tools such as SHAP.\
This report summarizes the end-to-end solution for both e-commerce and
credit card fraud detection.

# Data Analysis & Feature Engineering

We used two datasets:\
1. Fraud_Data.csv (e-commerce)\
2. creditcard.csv (banking)\
\
For the e-commerce data, additional geolocation features were engineered
by mapping IPs to countries. Other engineered features included
\`time_since_signup\`, \`hour_of_day\`, \`day_of_week\`, and
device-related usage patterns. The banking dataset contained anonymized
PCA components V1 to V28.

## Exploratory Data Analysis (EDA)

Key insights:

• Fraud is more prevalent during specific hours and weekdays.\
• Chrome and Safari had the most fraudulent transactions.\
• Most frauds occurred in records with unknown countries.\
• Fraud is uniformly distributed across days and times.\
• Purchase values for fraud vs. non-fraud are similarly distributed.

# Class Imbalance Handling

Both datasets exhibited strong class imbalance. To address this, we
applied:\
- SMOTE oversampling for e-commerce\
- Class weighting for credit card dataset\
\
These strategies improved recall and precision on minority (fraud)
class.

# Modeling & Performance

We trained Logistic Regression and Random Forest classifiers on both
datasets. PR AUC was used as the main evaluation metric due to the class
imbalance. Results:\
\
• Credit Card Dataset:\
- Logistic Regression: PR AUC = 0.7112\
- Random Forest: PR AUC = 0.8102\
\
• E-commerce Dataset:\
- Logistic Regression: PR AUC = 0.4076\
- Random Forest: PR AUC = 0.6226\
\
Random Forest consistently outperformed Logistic Regression in both
domains.

# Explainability with SHAP

We used SHAP to interpret Random Forest model outputs. Key global
drivers included \`purchase_value\`, \`age\`, and \`time_since_signup\`.
SHAP summary, beeswarm, and waterfall plots were used to visualize both
global and local interpretations.

# Partial Dependence Plots (PDP)

PDPs helped visualize how specific features (e.g., \`is_weekend\`,
\`time_since_signup\`) impact fraud predictions. These findings aligned
with SHAP insights.

# Final Model Choice

Random Forest was selected as the best model across both domains due to
its strong performance, robustness to noise, and compatibility with SHAP
explanations. While Logistic Regression provided interpretable
baselines, it lacked predictive power on the imbalanced datasets.

# Business Implications

Deploying these models will help Adey Innovations detect fraud more
accurately while maintaining a smooth customer experience. The use of
SHAP ensures transparency, making the system auditable and trustworthy
for stakeholders.

# GitHub Repository

All code, README instructions, and assets are available at:
https://github.com/miskerbab/fraud-detection-ecommerce-banking

# Appendix: Visualizations

![](media/image1.png){width="5.5in" height="3.6666666666666665in"}

Figure 1: Distribution of Fraudulent vs Non-Fraudulent Transactions

![](media/image2.png){width="5.5in" height="3.6666666666666665in"}

Figure 2: Fraud Cases by Browser

![](media/image3.png){width="5.5in" height="3.6666666666666665in"}

Figure 3: Fraud Cases by Country

![](media/image4.png){width="5.5in" height="2.75in"}

Figure 4: Fraud Cases by Day of Week

![](media/image5.png){width="5.5in" height="2.75in"}

Figure 5: Fraud Cases by Hour of Day

![](media/image6.png){width="5.5in" height="3.6666666666666665in"}

Figure 6: Fraud Cases by Traffic Source

![](media/image7.png){width="5.5in" height="3.6666666666666665in"}

Figure 7: Purchase Value by Fraud Class

![](media/image8.png){width="5.5in" height="3.6666666666666665in"}

Figure 8: PR Curve - Logistic Regression (Credit Card)

![](media/image9.png){width="5.5in" height="3.6666666666666665in"}

Figure 9: PR Curve - Random Forest (Credit Card)

![](media/image10.png){width="5.5in" height="3.6666666666666665in"}

Figure 10: PR Curve - Logistic Regression (E-Commerce)

![](media/image11.png){width="5.5in" height="4.125in"}

Figure 11: PR Curve - Random Forest (E-Commerce)

![](media/image12.png){width="5.5in" height="3.1565212160979876in"}

Figure 12: SHAP Beeswarm Plot - Credit Card

![](media/image13.png){width="5.5in" height="3.1565212160979876in"}

Figure 13: SHAP Summary Bar - Credit Card

![](media/image14.png){width="5.5in" height="1.6438353018372704in"}

Figure 14: SHAP Waterfall Plot - Credit Card

![](media/image14.png){width="5.5in" height="1.6438353018372704in"}

Figure 15: SHAP Force Plot - E-Commerce

![](media/image15.png){width="5.5in" height="3.6307994313210847in"}

Figure 16: Partial Dependence Plots - Random Forest

# 📌 Additional Model Insights & Final Interpretations

FRAUD CASE ANALYSIS (Index: 4)\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
Transaction details:\
purchase_value: 10.593280914634784\
age: 30.0\
hour: 20.0\
is_weekend: 0.0\
is_night: 1.0\
time_since_signup: 90.66656720551366\
is_new_user: 0.0\
is_high_value: 0.0\
user_transaction_count: 8.0\
device_unique_users: 1.0\
is_shared_device: 1.0\
is_young_user: 0.0\
is_ad_source: 0.0\
\
Model predictions:\
Random Forest: 0.060\
XGBoost: 0.020\
LightGBM: 0.136

✅ NON-FRAUD CASE ANALYSIS (Index: 0)\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
Transaction details:\
purchase_value: 8.73942445366517\
age: 51.0\
hour: 5.0\
is_weekend: 0.0\
is_night: 0.0\
time_since_signup: 67.2669992344283\
is_new_user: 0.0\
is_high_value: 0.0\
user_transaction_count: 6.0\
device_unique_users: 2.0\
is_shared_device: 1.0\
is_young_user: 0.0\
is_ad_source: 0.0\
\
Model predictions:\
Random Forest: 0.150\
XGBoost: 0.067\
LightGBM: 0.249

📋 MODEL INTERPRETABILITY REPORT\
====================================\
\
📊 EXECUTIVE SUMMARY:\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
The SHAP analysis reveals key patterns in fraud detection:\
• High-value transactions are the strongest fraud indicator\
• New users pose significantly higher fraud risk\
• Temporal patterns (night-time) affect fraud probability\
• Device sharing increases fraud likelihood\
• User demographics provide important risk signals\
\
🔍 MODEL CONSISTENCY ANALYSIS:\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
Top 5 features by model:\
Rank 1: is_weekend, time_since_signup, device_unique_users\
Rank 2: is_shared_device, purchase_value, time_since_signup\
Rank 3: device_unique_users, is_weekend, purchase_value\
Rank 4: is_young_user, device_unique_users, is_weekend\
Rank 5: time_since_signup, age, is_shared_device\
\
Features consistent across all models: \[\'is_weekend\',
\'device_unique_users\', \'time_since_signup\'\]\
\
📈 FEATURE STABILITY ANALYSIS:\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
\
is_weekend:\
Mean SHAP: 0.0000\
Std SHAP: 0.0571\
Range: \[-0.1674, 0.1674\]\
Stability score: 0.00\
\
device_unique_users:\
Mean SHAP: 0.0000\
Std SHAP: 0.0475\
Range: \[-0.2179, 0.2179\]\
Stability score: 0.00\
\
time_since_signup:\
Mean SHAP: 0.0000\
Std SHAP: 0.0323\
Range: \[-0.1324, 0.1324\]\
Stability score: 0.00\
\
🎯 MODEL RELIABILITY ASSESSMENT:\
\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\--\
Feature consistency score: 60.0%\
Reliability level: Medium - Models show moderate agreement\
\
✅ INTERPRETABILITY CONFIDENCE: HIGH\
The SHAP analysis provides reliable insights for business
decision-making.
