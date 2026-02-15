Track 1 – Data Sources and Data Architecture
Expected Source Tables

In a real company environment, customer churn modeling would rely on multiple structured data sources rather than a single flat file. The following source tables would likely be required:

1. Customer Master Table
One row represents one customer.
Contains customer_id, account start date, demographic attributes, contract type, and status indicators.

2. Billing Transactions Table
One row represents one billing event or one invoice.
Contains customer_id, billing_date, monthly charges, extra data fees, refunds, and payment method.

3. Service Usage Table
One row represents one customer per month or one usage event.
Contains customer_id, usage_date, data consumption, service adoption flags, and overage events.

4. Customer Support Table
One row represents one support interaction.
Contains customer_id, ticket_date, issue category, refund issued, resolution status.

5. Contract and Plan Table
One row represents one active plan per customer.
Contains plan_type, contract_term, internet_technology, and pricing tier.

Keys to Connect the Data

The primary key across tables would be customer_id.

Additional join keys would include:

account_id (if customers can have multiple accounts)

billing_date or month

service_date

event_timestamp

Time alignment is critical to ensure features are built using only information available before churn occurs.

Data Risks and Mitigation

One major risk is data leakage, where features include information that only becomes available after a customer has already churned. This risk can be reduced by enforcing strict time-based feature construction and validating that all features are available prior to churn labels.

Another risk is duplicate or inconsistent customer identifiers across systems. This can be mitigated by establishing a master customer identity table and enforcing referential integrity checks during data ingestion.
