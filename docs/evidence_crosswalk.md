# Manuscript-to-repository crosswalk

The table maps the appendix labels used by the manuscript to the released supplementary records. A row establishes traceability to the manuscript claim; it does not enlarge that claim beyond the reported task sets.

| Appendix label | Repository evidence | What the released record supports |
|---|---|---|
| `app:protocol` | `data/event_accounting.csv`; `data/system_measurements.csv`; `docs/implementation_rules.md` Section 8 | Event validity, assigned-run versus valid-event denominators, system totals, and evaluator-only information boundary |
| `app:task-accounting` | `data/task_set_accounting.csv`; `data/mechanism_outcomes.csv`; `data/context_comparison.csv` | Configuration counts, seeds, intervention timing, independent/reused relationships, and the associated outcomes |
| `app:secondary-results` | `data/context_request_audit.csv`; `data/context_comparison.csv` | Exact request counts, content overlap, and focused context checks |
| `app:paired-uncertainty` | `data/paired_uncertainty.csv` | Paired effects, exploratory intervals, resampling unit, replicate count, and bootstrap seed |
| `app:runtime-semantics` | `docs/implementation_rules.md` Sections 2-3 | Relation replacement, non-closed-world ledger behavior, goal reopening, and retained-hypothesis codes |
| `app:coordination-details` | `docs/implementation_rules.md` Sections 4-6 | Triggering, simultaneous reports, compatibility checks, authorization, and joint-tick behavior |
| `app:model-settings` | `docs/implementation_rules.md` Section 1 | Model-generation settings and method-specific decision limits |
| `app:scheduler-settings` | `docs/implementation_rules.md` Section 7 | Slot selection, ownership, local-first ordering, and approach/proposal limits |

## Main-text alignment notes

- Completion rates use all assigned runs; conditional rates are supplementary diagnostics.
- Reused context rows are not counted as independent new system executions.
- The request audit describes information exposure and does not define a new outcome metric.
- The paired intervals characterize the tested base configurations and are not population-wide performance guarantees.
- The rule document specifies the evaluated implementation behavior but does not independently provide the missing runtime, environment, or raw per-run logs.
