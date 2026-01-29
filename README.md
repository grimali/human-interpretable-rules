# Human-Interpretable Rules

This repository provides a rule-based variant explanation framework that generates trace-level, human-interpretable explanations for process variants.  

Here, we focus exclusively on the computation and evaluation of explainability-oriented metrics for these rule-based explanations.  

If you are interested in the full implementation of the pipeline, please visit:  
[rule-based-interpretations-of-trace-variants](https://github.com/fatiAblal/rule-based-interpretations-of-trace-variants)

---

---
# Evaluation Metrics

We assess the quality of rule-based explanations using standard interpretability criteria:

- **Fidelity**  
  Measures how well the rule-based explanations reproduce the target variant assignments.

- **Coverage**  
  Quantifies the fraction of traces for which at least one rule fires (i.e., its antecedent holds).

- **Simplicity**  
  Evaluates the cognitive load required to interpret the rule set, considering the number of rules, the mean/max number of conditions per rule, and the number of distinct behavioral features used.

- **Overlap**  
  Measures ambiguity in the explanations, i.e., the fraction of traces covered by multiple rules and the average number of firing rules per trace.

- **Robustness**  
  Assesses how stable explanations are under small perturbations of the trace-profile encoding, measuring both prediction agreement and similarity of fired rule sets.




## Usage Example

```python
from rule_metrics import evaluate_rules_with_label_matching

metrics, per_rule_df, per_rule_overlap_df = evaluate_rules_with_label_matching(
    dataset_csv_path="path_of_the_event_log.csv",
    decision_table_csv_path="path_of_the_decision_table.csv",
    stability_runs=30,
    stability_flip_prob=0.02,
    stability_seed=0
)

print(metrics)
print(per_rule_df.head())
print(per_rule_overlap_df.head())
