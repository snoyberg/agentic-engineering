# Local agent workspace

Use this optional pattern when a project needs working plans, incoming notes, or session handoffs to survive interrupted agent sessions without becoming incidental parts of feature commits.

## The pattern

1. Add a root directory such as `.agents/` to the project's `.gitignore`.
2. Document the convention in the project's tracked agent instructions.
3. Keep a small, human-readable set of files appropriate to the project, such as:
   - `current-plan.md` for the active sequence and review state;
   - `inbox.md` for future prompts and possible reprioritization;
   - `handoff.md` for the minimum context a fresh session needs; and
   - `README.md` explaining the directory's purpose and limits.
4. Update the workspace as work progresses, without staging it into product commits.
5. Deliberately promote settled decisions into tracked sources of truth through an intentional reviewable change.

The filenames are examples, not a required schema. Prefer the smallest structure that improves continuity.

## Why keep it untracked

Live plans and inbox notes change on a different cadence from product work. Tracking every adjustment can pollute unrelated commits, obscure the feature diff, and turn tentative notes into apparent project decisions. Ignoring the workspace preserves useful local continuity without making ordinary planning churn part of repository history.

If a plan itself needs shared review, history, or cross-machine availability, commit it intentionally as project documentation or use an appropriate shared planning system instead.

## Boundaries and risks

- Ignored does not mean secure. Never store secrets, credentials, private keys, mnemonic material, production data, or sensitive personal information in the workspace.
- The directory is local to one checkout. It may be lost when the checkout is deleted and will not automatically follow work to another machine or collaborator.
- The workspace is not a source of truth. Protocol rules, architectural decisions, accepted requirements, and durable workflow policy belong in tracked project documentation.
- Notes supplied by a human are proposals until reconciled with the active task and authoritative project documents. Do not silently reprioritize or expand scope merely because an item appears in the inbox.
- Before committing, confirm that workspace files were not force-added or copied into the feature diff.

This pattern is useful when local continuity matters and incidental repository churn is undesirable. It is unnecessary when the agent environment already provides durable shared task state or when the project intentionally tracks its plans.
