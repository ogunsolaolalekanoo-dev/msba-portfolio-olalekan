 Deployment and Monitoring Strategy
1. How would the model be deployed?

The churn model would be deployed as a batch scoring pipeline that runs daily or weekly. Customer data from the operational database would be extracted, transformed to match the feature engineering pipeline, and passed into the trained XGBoost model. The model would output churn probability scores between 0 and 1 for each customer.

These probabilities would then be stored in a database table that feeds the CRM system. Customers exceeding the operational threshold of 0.40 would be flagged for retention intervention.

2. What would be monitored after deployment?

Model performance must be monitored over time to ensure stability and reliability. Key monitoring metrics would include:

ROC-AUC on recent labeled data

Precision and recall at the 0.40 threshold

Overall churn rate trends

Feature distribution drift

If performance declines significantly or feature distributions shift materially, the model would require retraining.

3. What risks must be considered?

Potential risks include:

Data drift if customer behavior changes

Operational overload if too many customers exceed threshold

Over-reliance on static thresholds without reassessment

To mitigate these risks, the threshold and model performance should be reviewed quarterly.
