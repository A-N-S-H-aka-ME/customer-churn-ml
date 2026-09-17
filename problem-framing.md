# ML Problem-Framing Memo — Customer Churn

## 1. Decision
The business decision is whether a customer should be considered for a proactive retention intervention. The model is intended to support this decision; it should not automatically decide what treatment a customer receives.

## 2. Prediction target
The target is `churned`:
- `1` = churned
- `0` = did not churn

For a production deployment, the exact prediction horizon and label definition must be agreed before training. **Assignment assumption:** a 30-day action window is proposed for illustration because the supplied brief does not state a different horizon.

## 3. Unit of observation
One row represents one customer.

## 4. Available predictors
- `tenure_months`
- `support_tickets`
- `monthly_spend`
- `last_login_days`
- `plan_type`

`customer_id` is an identifier and should not be used as a predictive feature.

## 5. Action and human review
A high-risk prediction should create a review/eligibility signal rather than an automatic customer action. A human should confirm that an intervention is appropriate.

## 6. Non-ML baselines
Two baselines are appropriate:
1. **Majority class:** predict no churn for every customer. There are 7 non-churned and 5 churned customers, so this baseline has 58.3% accuracy on this dataset.
2. **Simple business rule:** predict churn when `last_login_days >= 10`. On these 12 rows this rule gives 11 correct predictions out of 12 (91.7%), with 4 true positives, 7 true negatives, 0 false positives and 1 false negative.

The second result should **not** be interpreted as evidence of production-level performance. The sample has only 12 observations, so a single threshold can look unusually strong by chance.

## 7. ML justification
Machine learning is worth testing as an educational baseline, but this dataset is too small to justify claims of generalizable production performance. A larger, representative, temporally valid dataset would be required before deployment.
