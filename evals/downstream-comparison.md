# Downstream Execution Comparison

Use this optional maintenance evaluation to test whether plans improved by `review-and-improve` lead to better execution—not just better-looking review reports. Do not run it during every plan review. Run it only when both plan variants can be executed safely in isolated copies of the same starting state.

## Protocol

1. **Freeze the case.** Record the user's original goal, explicit constraints/non-goals, acceptance criteria, exact plan version, relevant repository commit, and working-tree state. Save the unmodified plan as **A**.
2. **Create the treatment plan.** Review A with the skill. Have a human or independent evaluator accept, reject, or resolve proposed changes; preserve the original intent. Save the resulting plan as **B** and record the accepted delta. Do not silently rewrite A or let an executor see review-panel notes that are not in B.
3. **Prepare matched runs.** Create isolated copies/worktrees from the same repository snapshot. Give equivalent execution agents the same source brief, tools, model where possible, time/token budget, and acceptance tests. Each agent receives either A or B, not both; randomize or blind the labels for evaluators. Prevent shared mutable state between runs.
4. **Execute and capture evidence.** Let each agent follow its assigned plan. Record completed requirements, scope changes, clarification requests, consequential decisions it invented, verification results, regressions, and avoidable rework. Use the same acceptance tests and review rubric for both variants.
5. **Compare outcomes against the original intent.** Prefer B only when it improves required-outcome completion or reduces unsupported decisions/rework without increasing scope drift, verification gaps, or safety risk. Report the evidence and tradeoffs; do not infer a general guarantee from one case.
6. **Repeat when execution is stochastic.** Use multiple matched runs when feasible and report the number of runs and variance. A single matched pair is a useful case study, not statistical proof.

## Safety and limits

- Use disposable branches, worktrees, containers, or equivalent isolation. Never run an experimental comparison against production or allow destructive operations to escape the sandbox.
- If an execution needs secrets, irreversible changes, or external side effects that cannot be safely isolated, stop and use a non-executing tabletop review instead.
- A better review report is not evidence of better execution by itself. Preserve execution logs and test results so the comparison is auditable.

## Comparison summary

| Measure | Plan A: original | Plan B: reviewed | Evidence |
|---|---|---|---|
| Original acceptance criteria met | | | |
| Scope drift | | | |
| Clarification requests | | | |
| Unsupported consequential decisions | | | |
| Verification evidence | | | |
| Avoidable rework / regressions | | | |
| Safety or rollback gaps | | | |

Record the repository snapshot, execution-agent setup, run count, evaluator blinding, and limitations alongside the results.
