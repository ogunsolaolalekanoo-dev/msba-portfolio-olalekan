TruSource Customer Churn Prediction
Business Context

TruSource experiences a churn rate of approximately 26.5 percent, meaning more than one in four customers eventually leave. Because acquiring new customers is significantly more expensive than retaining existing ones, the business objective is to develop an early-warning system that prioritizes high-risk customers for targeted intervention.

Modeling Strategy

Data was splitted using stratified sampling to preserve churn rate distribution. Multiple models were evaluated using Stratified 5-Fold Cross-Validation, including Logistic Regression, Random Forest, Gradient Boosting, and XGBoost.

XGBoost achieved the highest cross-validated ROC-AUC (0.9002) and strong generalization performance on the holdout set (ROC-AUC: 0.8996–0.9086 depending on split).

Threshold optimization was performed to balance recall and precision. A probability cutoff of 0.40 was selected based on F1 maximization and operational tradeoff analysis.

Model interpretability was supported using feature importance and SHAP analysis.
Key Analytical Insights

Churn risk is concentrated early in the customer lifecycle.

Billing friction and extra data fees significantly increase churn probability.

Greater service adoption reduces churn risk.

Segment-specific retention strategies outperform blanket discounts.

How to Reproduce

Open the notebook.

Run cells sequentially from top to bottom.

The final section generates churn probabilities and holdout scoring output.

Limitation

The model relies on historical behavioral patterns and should be monitored over time for potential data drift.
## Model Evaluation Summary

The final model was evaluated using a stratified train-test split.  
Holdout ROC-AUC: 0.8996  
Confusion Matrix: TN=903, FP=131, FN=99, TP=274  

This confirms the model generalizes well to unseen data and captures approximately 73.5% of churners while maintaining reasonable precision and helping Tru-Source avoid over retention which saves money.
## Technical Stack
- Python
- Scikit-learn
- XGBoost
- Pandas
- NumPy
- SHAP
- Matplotlib


