# Risk Register — Customer Churn ML

| ID | Risk | Likelihood | Impact | Mitigation / control | Monitoring |
|---|---|---|---|---|---|
| R1 | False positive churn prediction | Medium | Medium | Human review before retention action; avoid automatic incentives | Precision, FP count, sampled reviews |
| R2 | False negative churn prediction | Medium | High | Track recall; inspect missed churn cases | Recall, FN count |
| R3 | Data leakage | High | High | Define prediction timestamp and feature cutoff; audit features | Leakage tests, temporal validation |
| R4 | Small sample size | High | High | Treat current results as educational only; collect more data | Dataset size and confidence intervals |
| R5 | Sampling/representation bias | High | High | Validate on a representative population and relevant subgroups | Subgroup coverage/performance |
| R6 | Privacy or inappropriate reuse | Medium | High | Minimize identifiers and restrict use/access | Access review, data-use audit |
| R7 | Over-reliance on predictions | Medium | High | Require human review and document uncertainty | Human override/review rate |
| R8 | Model drift | Unknown | Medium/High | Re-evaluate on recent labeled outcomes | Periodic performance monitoring |
| R9 | Incorrect intervention | Medium | Medium | Define approved interventions and rollback/escalation rules | Intervention outcomes and complaints |
| R10 | Target definition ambiguity | High | High | Lock label definition and prediction horizon before deployment | Label audits and documentation |
