# review-and-improve skill

A portable Agent Skill for reviewing implementation plans against the user's intent and checking whether an executor can carry them out without consequential guessing.

The review keeps two judgments independent:

- **Intent alignment:** does the plan preserve the user's goals, constraints, and later clarifications?
- **Execution readiness:** are the work, dependencies, acceptance criteria, and verification clear enough to proceed?

The skill produces evidence-backed findings and a concrete plan delta. It does not edit or execute the source plan by default. Reviewer panels are sized to risk; if the runtime cannot dispatch independent reviewers, the report must disclose the single-agent fallback.

## Install

Clone into a directory scanned by your agent runtime. For runtimes that support the shared Agent Skills directory:

```sh
git clone https://github.com/podo/review-and-improve-skill.git ~/.agents/skills/review-and-improve
```

Other runtimes may require placing the repository contents in their own skills directory. Keep `SKILL.md`, `references/`, and `evals/` together; the skill resolves its references relative to `SKILL.md`.

## Repository contents

- `SKILL.md` — review workflow, verdicts, report contract, and quality rubric.
- `references/reviewer-lenses.md` — risk tiers, panel allocation, and reviewer prompts.
- `references/finding-schema.md` — detailed ledger, finding, and verdict definitions.
- `evals/evals.json` — representative positive plan-review cases and expected behavior.
- `evals/downstream-comparison.md` — optional protocol for comparing execution outcomes from original and reviewed plans.

## Version

The initial release is **0.1.0** (`v0.1.0`).

## License

MIT. See [`LICENSE`](LICENSE).
