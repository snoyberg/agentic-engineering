# Bootstrapping a new user

Use this guide when someone arrives with little or no existing AI software-development environment.

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

## 5. Establish persistent agent guidance

Create repository-local agent instructions.

Reference this repository as upstream guidance where appropriate.

Record the user's own autonomy and review preferences separately.

If their AI tool supports persistent user-level instructions, use that mechanism for preferences that should apply to every project.

Do not assume that a tool supports a particular global-instruction mechanism. Inspect the tool's current capabilities.

## 6. Choose technology conservatively

Start from project requirements.

Prefer mature tools, boring deployment paths, strong automated checking, and technologies the available humans and agents can maintain.

Do not choose an elaborate architecture because the implementation cost appears cheap with AI.

Operational and conceptual complexity remain real costs.

## 7. Make the first experiment cheap

The availability of AI makes speculative prototypes more reasonable.

Use that advantage.

Do not respond by making prototypes architecturally extravagant.

Identify the riskiest assumption and build enough to learn whether it is true.

## 8. Build feedback loops

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

## 9. Record what you learn

When the user develops recurring preferences or the project discovers generally reusable practices, update persistent guidance.

If an improvement appears useful beyond this project, consider proposing it upstream.
