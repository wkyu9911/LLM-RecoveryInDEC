# Supplementary record for LLM recovery in dynamic embodied cooperation

This repository accompanies the manuscript **"Design Choices for LLM Recovery in Dynamic Embodied Cooperation."** It releases the compact data accounts and implementation rules referenced by the manuscript appendix.

## Evidence boundary

The repository contains:

- machine-readable task-set, event, request-audit, and paired-uncertainty accounts;
- the implementation rules needed to interpret the recovery controller and its experimental settings; and
- a crosswalk from manuscript appendix labels to released files.

It does **not** contain the full VirtualHome/C-WAH runtime, model credentials, private intervention routes, terminal-audit answers, or a claim that the complete experiment can be rerun from this repository alone. The rule document is a manuscript-linked specification of the evaluated implementation, not a substitute for the unavailable runtime snapshot. The released counts summarize the manuscript's frozen comparisons; they are not newly generated experiments.

## Repository layout

| Path | Contents |
|---|---|
| `data/task_set_accounting.csv` | Configurations, seeds, runs, and reuse relationships |
| `data/event_accounting.csv` | Assigned-run, valid-event, and conditional-success denominators |
| `data/context_request_audit.csv` | Saved-request audit for retained failure context |
| `data/paired_uncertainty.csv` | Paired effects and exploratory clustered-bootstrap intervals |
| `data/system_measurements.csv` | Completion, model-call, joint-step, and confirmed-token totals |
| `data/mechanism_outcomes.csv` | Scope-by-context completion counts |
| `data/context_comparison.csv` | Focused retained-versus-recent context checks |
| `docs/implementation_rules.md` | Ledger, triggering, compatibility, budget, and scheduler rules |
| `docs/evidence_crosswalk.md` | Manuscript-to-repository traceability |
| `manifest.sha256` | SHA-256 checksums for the released evidence files |

## Reading the data

The main completion metric is success over all assigned runs. `valid_events` records runs in which the intended disturbance was established; `successes_over_valid_events` is therefore a conditional diagnostic, not the primary outcome. Rows marked as reused are not independent new executions.

The paired intervals are exploratory. They resample base configurations after averaging paired seed differences, using 4,000 bootstrap replicates and seed 48021. They describe variation across the tested configurations and do not establish a population-wide ranking.

Joint-step and confirmed-token values are aggregate audit totals over assigned runs. They are not normalized latency or monetary-cost estimates.

## Citation

Please cite the associated manuscript. Bibliographic metadata will be added after publication.
