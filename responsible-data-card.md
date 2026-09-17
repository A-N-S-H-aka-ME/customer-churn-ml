# Responsible Data Card — Customer Churn Training Data

## Dataset purpose
This dataset is intended for educational development and evaluation of a customer-churn prediction model. It may support retention-related analysis. It must not be repurposed for unrelated high-impact decisions such as employment, lending, insurance eligibility, or other decisions not covered by the intended use.

## Provenance and permission
The dataset was supplied as the **Customer churn training data** in the Rabtech Academy assignment. The provided material does not document the original collection process, source systems, consent process, licensing terms, or retention/deletion policy. Those items are therefore **unknown** and should be confirmed before any real-world deployment.

## Population and representation
The supplied file contains 12 customer records and three plan types: Basic, Standard, and Pro. The sample is very small, and the sampling method and broader population are undocumented. No claim should be made that it represents all customers or customer segments.

Target balance:
- Churned: 5/12 (41.7%)
- Not churned: 7/12 (58.3%)

## Features and target
Features:
- `tenure_months`: customer tenure in months
- `support_tickets`: number of support tickets
- `monthly_spend`: monthly spending
- `last_login_days`: days since last login
- `plan_type`: Basic, Standard, or Pro

Target:
- `churned`: 1 or 0

Identifier:
- `customer_id`: identifier only; exclude from model training.

Potential leakage: every feature must be available before the prediction timestamp. Any information recorded after churn or after the decision point must be excluded.

Sensitive attributes are not present in the supplied columns. However, variables can act as proxies depending on how the underlying data was collected, so this cannot be ruled out without provenance/context.

## Quality checks
Check:
- missing values
- duplicate customer IDs
- invalid or impossible values
- outliers
- target/class balance
- train/test separation
- temporal leakage
- duplicate customers across splits

The dataset contains 12 rows, making statistical estimates highly unstable.

## Risks and safeguards
### False positives
A customer may be incorrectly flagged as at risk.
**Safeguard:** human review before intervention; avoid unnecessary or intrusive treatment.

### False negatives
A customer who later churns may not be flagged.
**Safeguard:** track recall and review missed churn cases.

### Sampling bias
The sample may not represent the wider customer population.
**Safeguard:** collect more representative data and evaluate relevant subgroups where appropriate.

### Privacy
Customer-level information may be sensitive.
**Safeguard:** minimize identifiers, restrict access, and use the data only for the documented purpose.

### Leakage
Post-outcome information can make evaluation unrealistically optimistic.
**Safeguard:** define the prediction timestamp and enforce feature cutoffs.

### Automation risk
Staff may treat a prediction as a fact.
**Safeguard:** make predictions decision-support signals, document uncertainty, and require review.

## Intended evaluation
Report:
- accuracy
- precision
- recall
- F1
- confusion matrix
- error analysis
- calibration if probabilities are used

False-positive and false-negative costs should be explicitly discussed rather than relying on accuracy alone.

## Limitations
This is a 12-row training exercise. Results are not evidence that a model will perform similarly on future customers. Production evaluation should use a substantially larger, representative, temporally separated dataset.
