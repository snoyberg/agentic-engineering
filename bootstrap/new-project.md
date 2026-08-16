# Bootstrapping a new project

Use this guide when a user already has a working AI development environment and wants to start a new software project.

This document is addressed to the AI agent helping the user.

## Start with the product question

Clarify what the project is trying to accomplish and what first experiment would produce useful evidence.

Do not default to architecture work before understanding the problem.

Prefer a narrow vertical slice that tests the riskiest assumption over a broad implementation of speculative requirements.

## Inspect existing guidance

Before making architectural decisions:

1. read the user's own persistent guidance or agentic-engineering repository, if available;
2. read relevant peer guidance the user intentionally follows, including this repository where appropriate;
3. inspect project-local instructions if the repository already exists;
4. identify explicit project deviations rather than silently overriding the user's defaults.

Peer repositories do not form an authority hierarchy. If they disagree, surface the disagreement and follow the current user's choices plus any explicit project-local decision.

## Choose a review and autonomy model

Record how the user wants agents to operate for this project, especially where it differs from their usual defaults.

Clarify authorization boundaries around remote writes, deployment, billing, production data, and destructive operations.

## Choose a proportional technology stack

When the user has no stronger preference, use `philosophy/technology-defaults.md` as a starting point rather than forcing them to make arbitrary technical selections.

Choose technologies based on the product, operational burden, available expertise, cost, and maintainability.

Prefer a stack that runs locally for development and testing.

For small web experiments, start by considering low-operations hosting such as Cloudflare Pages and Workers, with D1 when its current capabilities fit the data model. Verify current pricing and platform limits before relying on them.

Avoid Kubernetes, sprawling AWS topologies, and collections of always-on managed services for speculative projects unless there is a concrete requirement that justifies their complexity and cost.

## Establish quality feedback early

Create the cheapest useful combination of formatting, linting/static analysis, tests, CI, and staging appropriate to the project's risk.

Do not postpone all verification infrastructure until after a prototype becomes important.

Where deployment cost can grow with usage, configure sensible budgets, quotas, alerts, or hard limits when the provider supports them.

## Keep architecture proportional

Cheap code does not make operational complexity cheap.

Prefer simple deployment, explicit data models, mature dependencies, and straightforward boundaries.

Add distributed components, generalized frameworks, queues, caches, or additional services only when the problem justifies them.

## Keep project guidance local

The project's `AGENTS.md` or equivalent should explain project-specific facts and deliberate deviations.

Reference the user's guidance repository and other relevant peer repositories rather than mechanically copying all of their contents.

When reproducibility matters, prefer commit-specific permalinks. Copy or vendor selected material when archival durability, independence, or the risk of disappearing external content justifies doing so, and preserve provenance when practical.

If project work reveals a reusable improvement, classify it appropriately: keep project-specific facts here, update the user's guidance for personal preferences, or propose an issue or pull request to a peer repository whose guidance would benefit.
