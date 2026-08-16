# Bootstrapping a new project

Use this guide when a user already has a working AI development environment and wants to start a new software project.

## Start with the product question

Clarify what the project is trying to accomplish and what first experiment would produce useful evidence.

Do not default to architecture work before understanding the problem.

Prefer a narrow vertical slice that tests the riskiest assumption over a broad implementation of speculative requirements.

## Inspect existing guidance

Before making architectural decisions:

1. read the user's persistent guidance, if available;
2. read this repository's relevant engineering guidance;
3. inspect project-local instructions if the repository already exists;
4. identify explicit deviations rather than silently overriding upstream defaults.

## Choose a review and autonomy model

Record how the user wants agents to operate for this project, especially where it differs from their usual defaults.

Clarify authorization boundaries around remote writes, deployment, billing, production data, and destructive operations.

## Establish quality feedback early

Create the cheapest useful combination of formatting, linting/static analysis, tests, CI, and staging appropriate to the project's risk.

Do not postpone all verification infrastructure until after a prototype becomes important.

## Keep architecture proportional

Cheap code does not make operational complexity cheap.

Prefer simple deployment, explicit data models, mature dependencies, and straightforward boundaries.

Add distributed components, generalized frameworks, queues, caches, or additional services only when the problem justifies them.

## Keep local guidance local

The project's `AGENTS.md` or equivalent should explain project-specific facts and deliberate deviations.

Do not copy the entirety of upstream guidance into each project.

If project work reveals a reusable improvement, propose it at the appropriate upstream layer.
