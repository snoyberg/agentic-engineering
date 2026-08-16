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

Keep your personal guidance separate from Michael's upstream guidance.

Reference upstream recommendations where useful and record only your choices, additions, and disagreements locally.

You should be able to change upstream sources later without losing your own identity.

## Revisit the arrangement

Your preferences may change as you gain experience.

The agent should occasionally suggest updating persistent instructions when actual working behavior repeatedly differs from the written guidance.

Do not turn onboarding into a permanent questionnaire.
