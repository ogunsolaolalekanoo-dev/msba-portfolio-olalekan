**TruSource Churn Risk Modeling & Retention Intelligence Platform**

Winner – Spring 2026 Case Competition

**Executive Overview**

TruSource experiences a churn rate of approximately 26.5%, meaning more than one in four customers eventually leave. Because acquisition is significantly more expensive than retention, the objective of this project is to build a reliable early-warning system that prioritizes high-risk customers for targeted intervention.

This repository contains a complete churn modeling pipeline including preprocessing, cross-validation, threshold optimization, interpretability analysis, and holdout scoring.

**Modeling Pipeline**

-Data Preparation

-Feature engineering:

Lifecycle indicators (tenure groups, early-lifecycle flags)

Billing intensity features (avg_billed_per_month)

Friction signals (extra_data_fees_total, refunds_total)

Service depth metrics (services_addon_count)

-Behavioral aggregation signals

-Median imputation for numeric features

-One-hot encoding for categorical features

-Stratified train-test split


**Model Comparison (Stratified 5-Fold CV, ROC-AUC)**

**Model	CV ROC-AUC**
Logistic Regression	0.8875
Random Forest	0.8748
Gradient Boosting	0.8976
XGBoost	0.9002

**XGBoost** was selected based on highest cross-validated performance and stable holdout generalization.

**Final Model Performance**

Holdout ROC-AUC: 0.8996 – 0.9086
Holdout PR-AUC: 0.7828
Accuracy: 83.7%

Confusion Matrix (Threshold = 0.40 optimized):

True Negatives: 903

False Positives: 131

False Negatives: 99

True Positives: 274

Threshold 0.40 was selected based on F1 maximization and operational tradeoff analysis.

**Interpretability**

Feature importance analysis

SHAP summary and dependence plots

Segment-based churn pathway interpretation

**Deployment Considerations**

Batch scoring architecture

CRM integration

Threshold governance

Drift monitoring

**Repository Structure**
notebooks/   → Modeling pipeline
outputs/     → Holdout scoring artifacts
individual/  → Reflection and deployment analysis


**Project Structure**

├── notebooks/

│   └── churn_model.ipynb

├── outputs/

│   └── scored_holdout.csv

├── individual/

│   ├── contribution.md

│   ├── track1.md

│   └── track2.md

├── requirements.txt

└── README.md



**How to Reproduce**

Clone the repository.

Open notebooks/churn_model.ipynb.

Install required packages (example):

pip install pandas numpy scikit-learn xgboost shap matplotlib


Run the notebook top-to-bottom.

Final model evaluation (holdout metrics) will print near the end.

Scored holdout predictions will be saved to:

outputs/scored_holdout.csv


**Technical Stack**

Python

Pandas

NumPy

Scikit-learn

XGBoost

SHAP

Matplotlib

**Limitation**

Model performance is based on historical behavior patterns. Future shifts in usage, pricing, or customer behavior may require retraining and monitoring.
