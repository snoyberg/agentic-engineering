# Contributing

Issues and pull requests are welcome from both humans and AI-assisted workflows.

The repository is intentionally opinionated but not intended to become a universal standard.

## Good contributions

Useful contributions include:

- correcting an inaccurate recommendation;
- documenting a recurring failure mode;
- making an instruction clearer to humans or agents;
- adding evidence that supports, weakens, or changes a recommendation;
- identifying a security or trust-boundary problem;
- adding a peer repository with a meaningful relationship;
- documenting an alternative approach where disagreement is useful.

## Prefer evidence and rationale

When proposing a behavioral or engineering rule, explain why it helps and what problem it addresses.

Evidence that confirms an existing recommendation is useful too. A repeated success can justify stronger confidence, narrower caveats, or better examples even when the conclusion itself does not change.

A rule that merely reflects personal taste may belong in another person's peer repository rather than here.

## Agent-generated contributions

Agents are encouraged to notice reusable lessons and prepare proposals.

An agent should not represent its own preference as the user's settled position.

If an agent observed a recurring correction or pattern, say so and provide enough context for a human reviewer to judge whether the generalization is valid.

## Contributing from a project that references this repository

A project may reference P2P Agents by URL without keeping a local checkout. Treat the canonical URL, `https://github.com/snoyberg/p2p-agents`, as sufficient repository location.

When project work reveals a reusable improvement:

1. Classify the lesson before moving it upstream. Keep product behavior and project-specific exceptions in the project; propose only generally useful collaboration or engineering guidance here.
2. Obtain clear authorization before creating a branch, pushing, opening an issue, or opening a pull request in this repository. A request to prepare or open a P2P Agents pull request is sufficient; a general request to improve the current project is not.
3. If no checkout exists, clone the canonical repository into a temporary or otherwise clearly separate working directory. Read its current `AGENTS.md` and the task-relevant linked guidance before editing.
4. Make a focused change on an `agent/` branch, preserve unrelated state, and run checks appropriate to the changed documents.
5. Push the branch and open a draft pull request unless the user requested a different review state. Explain the project experience that motivated the proposal, why it generalizes, and what was checked.
6. Keep the originating project's change and the P2P Agents proposal independently reviewable. Link them when useful, but do not make either repository depend on an unaccepted change in the other.

Do not copy secrets, private repository context, unpublished product details, local planning notes, or other sensitive information into the upstream proposal. Summarize the reusable lesson with only the context needed to evaluate it.

## Keep changes reviewable

Keep unrelated ideas separate when practical.

Do not combine broad wording cleanup with substantive policy changes unless the changes truly need to move together.

The human maintainer decides what enters this repository.
