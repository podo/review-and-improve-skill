# Review Report and Finding Schema

Use this structure so an execution agent can act on the review without translating vague critique into plan edits.

## Required report

```markdown
# Plan review: <short plan name>

## Snapshot
- Plan: <source/path or inline version and identifying detail>
- Repository: <branch/commit and relevant working-tree state, if applicable>
- Sources reviewed: <paths/docs; note unavailable sources>

## Verdicts
- Intent alignment: aligned | partial | misaligned — <brief evidence-based reason>
- Execution readiness: ready | needs changes | blocked — <brief evidence-based reason>
- Recommendation: start | start after listed changes | do not start until decision/evidence is resolved

## Intent-to-plan ledger
| ID | User requirement / decision | Conversation evidence | Plan step | Verification | Status |

## Prioritized findings
| Priority | Finding / execution impact | Evidence | Affected step | Proposed amendment | Confidence / open question |

## Proposed plan delta
- Add: ...
- Remove: ...
- Clarify: ...
- Reorder: ...

## Unresolved decisions and limits
<Only material decisions, assumptions, missing evidence, failed/timed-out reviewers.>

## Panel execution
<Reviewer count and lenses by panel; disclose fallback, sequential dispatch, disagreement, or failure.>
```

Omit empty change categories; retain both verdicts, the recommendation, and reviewer limitations. Do not copy the entire original plan into the report unless the user asks for a revised draft.

## Verdict interpretation

- **Intent alignment — `aligned`:** no material conflict or omission between explicit user intent and the plan. **`partial`:** core direction matches, but material requirements or scope boundaries are missing or under-specified. **`misaligned`:** a material plan step contradicts a settled user goal, constraint, or later clarification.
- **Execution readiness — `ready`:** the plan can be executed and completion verified without consequential guessing. **`needs changes`:** bounded plan clarifications or additions are required, but no unresolved user decision or critical evidence gap prevents amendment. **`blocked`:** execution depends on a consequential decision, unavailable evidence, or safety prerequisite that must be resolved first.

Keep the axes independent: `aligned` does not imply `ready`, and a technically executable plan may still be `misaligned`.

## Ledger statuses

- `covered`: a plan step addresses the requirement and names adequate evidence of completion.
- `partial`: some part is covered, but a material part or verification is missing.
- `missing`: no plan step addresses the requirement.
- `conflict`: a plan step contradicts the requirement or a settled decision.
- `unverified`: a plan claim may address it, but available sources cannot confirm that claim.

For inferred requirements, label the inference and confidence. For unresolved consequential decisions, do not turn them into requirements; list them as questions.

## Finding quality

Include only findings that can change goal alignment, feasibility, implementation choices, verification confidence, or material risk. Each finding must name:

1. **Priority:** `critical`, `high`, `medium`, or `low`, based on consequence and likelihood. Critical/high findings normally block a start recommendation.
2. **Impact:** how it threatens user intent or downstream execution.
3. **Evidence:** a source locator (conversation turn, file/section, doc URL/section, or unavailable evidence) and the supported fact. The plan alone is not proof of intent.
4. **Affected step:** identify the numbered step or say that a required step is absent.
5. **Amendment:** a concrete `add`, `remove`, `clarify`, or `reorder` action. Do not prescribe unsupported implementation details.
6. **Confidence / question:** state meaningful uncertainty and ask the user only when the answer could materially change the plan.

Do not rank by reviewer votes. The coordinator resolves duplicate findings and reports genuine disagreements with their evidence.
