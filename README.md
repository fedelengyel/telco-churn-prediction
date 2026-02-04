# Project Overview
This project develops a machine-learning solution to predict customer churn in a telecommunications company, integrating a strong economic and managerial perspective.
The objective is not only to achieve statistical accuracy, but to understand how churn impacts revenue, customer lifetime value (CLV), retention costs, and optimal resource allocation.

# Two models were implemented and compared:
1. Logistic Regression (baseline, interpretable, linear decision boundary)
2. Random Forest (non-linear, higher economic efficiency under threshold tuning)
   
From an economic perspective:
False Negatives (FN) = customers who churn without being identified → real monetary loss in CLV.
False Positives (FP) = customers incorrectly flagged as churn → unnecessary retention cost.
The optimal model is the one that minimizes expected financial loss, not simply the one with highest accuracy.

# Data & Preprocessing
Source: Telco Customer Churn (Kaggle).
Key steps:
1. Cleaning inconsistent entries (e.g., converting TotalCharges to numeric).
2. Removing non-informative identifiers.
3. Binary encoding for Yes/No variables.
4. One-hot encoding for nominal categorical features.
5. Scaling for models requiring standardization.
6. Stratified train/test split to maintain class proportions.
This pipeline ensures no data leakage, proper transformation, and valid statistical inference.

# Modeling Strategy
1. Logistic Regression (baseline)
- Interpretable coefficients
- Useful to understand marginal effects
- Good AUC (≈0.84)
- Strong recall when using a lower threshold
Implication: retention costs inflate significantly
2. Random Forest (final chosen model)
- Captures non-linear interactions in customer behavior
- Better balance between FP and FN under threshold tuning
- More economically efficient:
    Slightly lower TP than logistic regression
    But dramatically fewer false positives, reducing unnecessary retention expenses
  
# Threshold Optimization (Economics-First)
Instead of using the standard 0.50 threshold, the final decision boundary was optimized to balance:
- Revenue protection (detecting churn early)
- Cost efficiency (avoiding excessive outreach)
At threshold = 0.35, the Random Forest reached:
1. High true positives (churn correctly identified)
2. Much lower false positives than Logistic Regression
3. A significantly better economic trade-off
This reflects a profit-maximizing approach, where the firm avoids overspending while still capturing most high-risk customers.

# Final Model Selected: Random Forest (thr = 0.35)
Why this model?
Maximizes net economic benefit:
- TP only slightly lower than Logistic Regression
- FP drastically lower → reduces unnecessary interventions
- Better for large-scale retention programs:
- Lower operational cost
- Less customer dissatisfaction from “false alarms”

# Final Performance Metrics (Random Forest @ 0.35):
- Recall: ~90% (captures most churners)
- Precision: ~52% (acceptable given cost structure)
- ROC-AUC: 0.86
  
# Technologies Used
Python
Pandas, NumPy
Scikit-learn
Seaborn, Matplotlib
Statistical modeling + Economic evaluation. Asi te parece bien? el texto tiene que ser asi de formato, no le pongas cuadros, ni emogis, ni tanta data
