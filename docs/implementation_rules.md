# Implementation rules recorded for the manuscript evaluation

This file records the implementation-level semantics and fixed settings referenced by the manuscript. It is a specification of the evaluated controller, not an executable release of the full C-WAH/VirtualHome runtime.

## 1. Model and decision limits

- Recorded model alias: `deepseek-flash`.
- Generation: temperature `0`, `top_p=1`, thinking disabled, and a 1,024-token output cap.
- LLM-Recovery: at most four recovery decisions per run, eight request attempts, and four operations per proposal.
- Adapted CoELA: at most 120 requests across planning, communication, and recovery.
- System runs allow at most 250 submitted joint steps.

The budgets reflect the systems' different divisions of labor. They should not be interpreted as identical per-decision roles.

## 2. Evidence-ledger update semantics

- Re-observing a relation source replaces stored `ON` and `INSIDE` relations from that source.
- Re-observing either endpoint replaces stored `HOLDS` relations involving that endpoint.
- Relations not contradicted by re-observation may persist; the ledger is not closed-world.
- Goal verification and reopening use the manuscript's relation-verification equation. An action receipt alone does not complete a task slot.

These rules preserve unrefuted public evidence while allowing direct re-observation to replace stale spatial or possession relations.

## 3. Failure-context retention

The retained-hypothesis state is instantiated only from grasp-phase feedback codes:

- `GRAB_NOT_OBSERVED`
- `ESCALATE_NO_OBSERVED_PROGRESS`

The recent-feedback comparison omits retained hypotheses but preserves the same observation and current-feedback channels. Retained hypotheses are therefore additional context, not a replacement for current evidence.

## 4. Recovery triggering and report ordering

- Only a report associated with a pending task may trigger recovery.
- Completion cancels stale reports for that task.
- Simultaneously eligible reports are handled in stable agent order.
- Recovery is bounded by the decision and request limits above.

## 5. Task-edit compatibility and authorization

For `rebind`:

- the replacement must be class-compatible with the required object;
- it must be unbound to another conflicting task;
- no conflicting agent may currently hold it; and
- its current source must not itself be held.

For `reassign`:

- the proposed owner must agree with observed possession when possession is known; and
- the recipient must be available for the resulting delivery responsibility.

Task-level authorization remains fixed for the proposal. Operation preconditions are refreshed from current evidence immediately before native execution. Accepted edits preserve the task identifier, reset the affected execution state, and return control to the ordinary scheduler.

## 6. Joint execution semantics

- A nonconflicting physical repair operation may share a joint tick with the teammate's ready routine work.
- Logical edits such as rebinding or reassignment consume no physical tick.
- Inspection, approach, opening, retry, and wait execute through the native helper and return ordinary execution receipts.
- A failed receipt terminates the current proposal with the corresponding disposition; it is not silently converted into task completion.

## 7. Scheduler and search settings

- The scheduler selects the first pending bound slot for each owner.
- Initial ownership alternates across the fixed task construction.
- Search is local-first: visible candidates and candidates whose current-room probability is at least `0.5` precede other candidates.
- Remaining ties are resolved first by locality and then by probability.
- An approach segment permits at most 12 walk attempts.
- A proposal contains at most four operations.

These limits were frozen for the reported comparisons and were not tuned by the scope/context ablation.

## 8. Evaluator-only information

Private intervention routes and the independent terminal audit remain outside the policy input. Audit answers are never returned to the recovery policy. The policy receives local observations, public evidence, reconciled task status, execution feedback, and public notices of environmental change.
