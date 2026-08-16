# Bootstrapping a new user

Use this guide when someone arrives with little or no existing AI software-development environment.

This document is addressed to the AI agent helping that person.

Do not perform every step mechanically. Determine what is already configured.

## 1. Understand the project

Ask the user what they are trying to build.

Focus initially on:

- the problem;
- intended users;
- what would constitute a useful first experiment;
- important constraints;
- obvious security, financial, privacy, or regulatory risks.

Do not begin with technology selection unless the technology is itself the purpose of the project.

Favor the smallest implementation that can test the important assumption.

## 2. Understand the user's working style

Read `people/adapting-to-you.md`.

Establish enough about the user's desired involvement to avoid either overwhelming them or taking unwanted control.

Do not require them to make technical decisions they do not understand merely for the appearance of human oversight.

## 3. Establish ownership

Whenever practical, the human or their organization should own:

- the GitHub account;
- repositories;
- domains;
- cloud accounts;
- billing relationships;
- production credentials.

Do not create long-term technical dependence on Michael, an AI vendor, or an individual developer merely because they are helping bootstrap the project.

## 4. Establish source control

If necessary, guide the user through creating and securing a GitHub account.

Use appropriate authentication supported by their environment.

Never ask the user to paste long-lived secrets into repository files or agent instructions.

Create a repository early enough that meaningful work is versioned.

## 5. Establish the user's own agentic-engineering repository

If the user intends to build more than a one-off experiment, recommend creating a small repository for their persistent agent guidance before creating many project-specific rules.

That repository should belong to the user or their organization. It can begin with only a README and an agent entry point. Record the user's autonomy choices, technical preferences, recurring corrections, and deliberate differences from Michael's recommendations as they emerge.

Reference Michael's repository and any other useful peer repositories instead of presenting their preferences as the user's own. When reproducibility matters, use a commit-specific permalink. Copy selected guidance when the user deliberately wants an independent or durable snapshot.

Do not block useful work if the user is not ready to maintain a dedicated guidance repository. Start with the persistent mechanism their current tool supports and migrate later if the pattern proves valuable.

## 6. Establish project-local agent guidance

Create repository-local agent instructions for the actual project.

The project should normally reference the user's agentic-engineering repository and may reference other peer guidance repositories where relevant.

Keep project-specific facts and exceptions local: architecture decisions, build commands, deployment details, domain rules, current constraints, and deliberate deviations from the user's defaults.

Do not copy large bodies of peer guidance into each project merely for convenience. Do copy or vendor material intentionally when archival durability, independence, or protection against disappearing external content matters.

## 7. Choose technology conservatively

Start from project requirements and read `technology/defaults.md` when the user has no stronger preference.

Prefer mature tools, boring deployment paths, strong automated checking, and technologies the available humans and agents can maintain.

Do not choose an elaborate architecture because the implementation cost appears cheap with AI.

Operational and conceptual complexity remain real costs.

## 8. Choose a low-cost deployment path

Assume a person experimenting with a new product may not have production infrastructure experience or the ability to manage complex cloud cost controls.

Develop and test locally first whenever practical.

For a small web experiment, Cloudflare Pages and Workers are strong starting points because they can support useful public deployments with relatively little operational machinery. D1 is worth considering when a Cloudflare-native relational store fits the workload.

Verify current pricing, free-tier limits, quotas, and runtime constraints before relying on them. Platform economics change.

Avoid defaulting a speculative project to Kubernetes, a sprawling AWS architecture, or multiple always-on managed services. If a heavier platform is genuinely required, explain why and make the likely cost model visible to the user.

Where providers support budgets, quotas, alerts, or hard limits, configure sensible protections before exposing an experimental service to unpredictable traffic.

## 9. Make the first experiment cheap

The availability of AI makes speculative prototypes more reasonable.

Use that advantage.

Do not respond by making prototypes architecturally extravagant.

Identify the riskiest assumption and build enough to learn whether it is true.

## 10. Build feedback loops

Before increasing agent autonomy, establish the mechanisms that make mistakes visible:

- version control;
- automated tests;
- linting/static analysis;
- CI;
- staging when appropriate;
- logs and observability;
- backups for persistent state;
- reviewable changes.

Automation should increase the amount of safe experimentation, not merely the amount of code produced.

## 11. Record what you learn

When the user develops recurring preferences or the project discovers generally reusable practices, update persistent guidance.

If an improvement appears useful to another person's agentic-engineering repository, suggest a pull request or discussion with that peer rather than treating one repository as an authority over the other.
