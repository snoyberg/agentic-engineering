# Repository relationships

Agent-guidance repositories are peers.

Do not model one person's guidance repository as upstream and another person's as downstream merely because one influenced the other. A peer may borrow heavily from another peer, disagree with it, send changes back, or later become the source of ideas that flow in the opposite direction.

Concrete software projects are different: a project's local agent instructions may reference one or more peer guidance repositories as sources of general engineering and collaboration preferences.

## Referencing peer guidance

When a project or guidance repository references external instructions:

- prefer a commit-specific permalink when reproducibility matters;
- retain enough provenance to know whose recommendation is being used and why;
- distinguish deliberate adoption from a link included only for comparison;
- do not treat the referenced repository as having authority over the current user.

A moving branch link is reasonable when the explicit goal is to track that peer's evolving recommendations. A commit permalink is better when the current behavior must remain reproducible.

## Copying guidance

Links are often preferable because they preserve provenance and allow ideas to evolve independently, but copying is sometimes the better engineering choice.

Copy or vendor selected material when:

- the project must remain usable if the original repository disappears;
- an archival or regulatory requirement demands a local snapshot;
- the project deliberately wants to freeze a version and modify it independently;
- network access to the original source cannot be assumed.

When copying, record the original source and commit when practical. Once copied and modified locally, treat the local text as the project's responsibility rather than silently resynchronizing it.

## How ideas flow

When project work or a peer repository reveals a reusable lesson:

- keep project-specific facts in the project;
- record person-specific preferences in that person's guidance repository;
- send generally useful improvements to any peer repository whose recommendations they improve;
- document genuine disagreement instead of forcing convergence.

Evidence can support an existing recommendation as well as challenge it. Repeated success, repeated failure, and contextual differences are all useful information.

There is no designated root repository. The network should become more useful as independent peers reference, challenge, and improve one another.
