# Technology defaults

These are Michael Snoyman's current default technology choices for new projects. They are starting points, not mandates.

Use project requirements, deployment constraints, available expertise, and operating cost to override them deliberately.

## Languages

### Rust

Prefer Rust for backend services, CLIs, infrastructure tooling, protocol implementations, cryptography, data processing, and other systems where correctness and maintainability matter.

Favor the stable toolchain and a current edition unless compatibility requirements say otherwise.

Common Rust choices:

- `serde` / `serde_json` for serialization;
- `reqwest` for HTTP clients;
- `clap` for CLIs;
- `anyhow` with context at application and operational boundaries;
- `thiserror` for typed library/domain errors;
- `tracing` and `tracing-subscriber` for diagnostics;
- `tokio` where asynchronous I/O is needed;
- `axum` for ordinary HTTP APIs;
- `sqlx` for relational database access, using compile-time-checked queries where supported.

Prefer explicit domain types, narrow effects, ordinary functions, and strong linting over elaborate type-level or macro machinery.

### TypeScript

Use TypeScript rather than plain JavaScript for substantial browser or Node.js application logic when Rust/WASM is not a better fit.

Do not choose JavaScript merely because a prototype is temporary; cheap type checking has a strong power-to-weight ratio.

### Haskell

Haskell remains appropriate where its ecosystem or functional abstractions materially fit the problem, but it is no longer the default for greenfield general-purpose application development.

### Solidity and smart contracts

Use Solidity for EVM smart contracts and Foundry for contract testing and local EVM workflows unless the project has a concrete reason to choose another stack.

For Rust EVM integration, prefer Alloy over adding new ethers-rs APIs.

## Frontend

For Rust-centric applications, Leptos is a reasonable default for a client-side Rust/WASM application when keeping frontend logic in Rust has real value.

For conventional web applications where ecosystem breadth and hiring familiarity matter more, TypeScript is a reasonable default. Choose a frontend framework based on the project rather than treating one framework as doctrine.

Prefer accessible, responsive interfaces with restrained dependencies and simple build pipelines.

## Persistence

Prefer relational storage unless the data model clearly calls for something else.

- SQLite is an excellent default for local tools, prototypes, single-node services, and applications whose concurrency requirements fit it.
- Cloudflare D1 is a useful low-operations SQLite-like option for Cloudflare-hosted prototypes.
- PostgreSQL is the default when a conventional multi-user server requires a full relational database.

Use migrations from the beginning once persisted state matters.

Do not introduce multiple databases, caches, queues, or search systems until there is evidence that the simpler architecture is insufficient.

## Hosting and deployment

For speculative products and prototypes, optimize for low fixed cost and low operational burden as well as developer speed.

Prefer architectures that can run locally for development and testing and can be deployed to a provider with a generous free or low-cost tier.

Cloudflare is a strong default starting point:

- Pages for static sites and frontend assets;
- Workers for lightweight APIs and server-side logic;
- D1 where its database model fits;
- KV or R2 only when their semantics match an actual requirement.

Do not reach first for AWS, Kubernetes, or a multi-service cloud architecture for an experiment. They are valid tools when scale, compliance, existing infrastructure, or specific managed services justify their operational and cost complexity.

When Cloudflare is a poor fit, choose another simple managed platform before assembling bespoke infrastructure.

Before introducing paid infrastructure, understand likely idle cost, scaling behavior, bandwidth/storage cost, and whether the user can safely control spend.

## Containers and infrastructure

Use Docker where reproducible packaging or deployment benefits from it, but do not require containers for software that is simpler to run directly.

Use infrastructure-as-code once infrastructure is important enough that reproducibility matters. Avoid creating a large infrastructure layer merely to deploy a small experiment.

## Quality tooling

Enable cheap automated correctness mechanisms early:

- formatting;
- compiler warnings and strict lints;
- dependency auditing where useful;
- tests targeted at meaningful behavior;
- CI on pull requests;
- integration or deployment smoke tests when infrastructure boundaries are important.

For Rust, `cargo fmt`, Clippy with warnings denied where practical, and `cargo test` are baseline expectations.

## Selection rule

When a user says "I don't know what to use; I just want to build this app," start with these defaults and simplify further when possible.

Do not force the user to choose among technologies they do not understand. Explain only the decisions that materially affect product behavior, cost, ownership, risk, or future options.

Record deliberate deviations in the project's agent instructions so future agents preserve the choice rather than repeatedly reopening it.
