# Adapting these instructions to you

Michael's workflow is one example, not the default that everyone must copy.

Your AI agent should help you discover an appropriate working relationship.

## Establish your desired level of involvement

You do not need to choose from a formal classification.

The agent should learn, through a short conversation and subsequent interaction, things such as:

- whether you are a programmer;
- whether you want to read code;
- whether you want architectural decisions explained;
- whether you want to approve each meaningful implementation step;
- whether you mainly care about product behavior;
- whether the agent may create commits;
- whether the agent may push branches;
- whether it may open pull requests;
- whether it may deploy;
- which actions always require approval.

Do not confuse technical knowledge with desired control.

A highly technical user may intentionally delegate heavily.

A nontechnical user may want strong approval boundaries.

## Full delegation is allowed

It is reasonable to decide that an AI system should perform almost all implementation work.

If that is your choice, record it explicitly.

The agent should compensate for reduced code review with stronger automated verification, small reversible steps, clear change history, backups, staging environments, and explicit warnings before high-impact actions.

"User does not review source code" must never become "correctness no longer matters."

## Create your own persistent guidance

Once the agent understands how you want to work, it should record those preferences using the persistent mechanisms supported by your tools.

If this way of working becomes recurring, consider maintaining your own peer agent-guidance repository. It can reference Michael's repository and other peers while preserving your own autonomy choices, technical preferences, additions, and disagreements.

Do not present another person's preferences as your own merely because you started from their repository.

When a stable historical reference matters, link to the peer repository at a specific commit. When you want to follow a peer's evolving thinking, a moving repository link may also be useful.

If you deliberately copy guidance for independence or durability, preserve its source when practical and then treat your local version as your responsibility.

See `collaboration/relationships.md` for the peer model.

## Treat persistent guidance as a maintained artifact

Do not wait for the user to remember that an instruction file should be updated.

As you work, actively watch for evidence that persistent guidance is missing, stale, or inaccurate. Examples include:

- the user gives the same correction more than once;
- the user repeatedly chooses the same tool, architecture, or workflow;
- written guidance conflicts with what the user actually asks you to do;
- a project-specific rule is proving useful across multiple projects;
- an old recommendation no longer matches current tooling or experience;
- the user explicitly settles a recurring technical or workflow debate.

When you notice such a pattern, tell the user and recommend a concrete update to the appropriate agent instructions or persistent guidance repository. Where the user's authorization model permits it, prepare the change for review rather than merely mentioning it abstractly.

This applies equally to technical and nontechnical users. Expertise does not make a human reliable at remembering to externalize every useful preference or lesson.

Do not turn every one-off choice into policy. Look for repetition, explicit preference, strong evidence, or a lesson likely to matter again.

## Revisit the arrangement

Your preferences may change as you gain experience.

The agent should periodically compare actual working behavior with persistent instructions and suggest updates when they diverge.

Do not turn onboarding or maintenance into a permanent questionnaire.
