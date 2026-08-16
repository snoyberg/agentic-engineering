# Technology defaults

These are Michael Snoyman's current default technology choices for new software projects. They are instructions to agents, not a requirement that every project use the same stack.

Start here when the user has no strong technology preference. Deviate when product requirements, team experience, ecosystem constraints, deployment targets, or measured evidence make another choice better. Record meaningful deviations in the project's own agent instructions.

Do not cargo-cult this list. Prefer the smallest coherent stack that solves the current problem.

## Languages

### Rust

Prefer Rust for new backend services, command-line tools, systems work, protocol implementations, security-sensitive code, data-processing tools, and substantial automation.

Use the current stable Rust edition unless compatibility requirements say otherwise. Prefer a workspace for multi-crate projects and centralize shared dependency versions at the workspace root.

Strong typing is a means to correctness, not a goal by itself. Prefer simple domain types, enums, pattern matching, and checked conversions over elaborate type-level machinery whose maintenance cost exceeds its practical benefit.

### TypeScript

Prefer TypeScript over JavaScript for substantial browser application code when using the JavaScript ecosystem.

For a new browser application where the user has no personal preference, React + Vite with strict TypeScript is the safer general default because of ecosystem breadth, tooling support, developer familiarity, and staffing flexibility. TanStack Query and TanStack Router are reasonable defaults when their problems are present; do not add them merely because they are familiar.

Use a fast formatter/linter such as Biome when it fits the project. Prefer `pnpm` for Node package management unless the project already standardizes on another tool.

### Rust in the browser

Michael personally prefers Leptos and may choose it as an intentional use of novelty budget, especially in Rust-heavy projects where sharing types or logic with Rust materially simplifies the system or where keeping most implementation in Rust has real value.

Do not generalize that preference automatically to other users. For someone who simply wants to build a web application and has no strong stack preference, React + TypeScript is normally the more conservative recommendation because of ecosystem breadth, tooling support, developer familiarity, and staffing flexibility—not because Leptos being mature or lightly maintained is inherently a negative.

When choosing Leptos, consider `leptos_router` for routing and `leptos-fetch` for client-side async state/data fetching when those needs are present. Verify compatibility and current ecosystem health before relying on ecosystem crates.

Leptos being mature and feature-complete is compatible with choosing it deliberately. The relevant tradeoff is primarily ecosystem size, tooling, available developers, and integration surface versus the advantages of keeping a Rust-heavy application in one language and type system.

Do not choose Rust/WASM merely to avoid TypeScript. Browser ecosystem integration, bundle size, developer familiarity, and product requirements still matter.

### Other languages

Haskell, C, and C++ should require strong project-specific motivation over Rust for new greenfield work. Existing codebases, required ecosystems, FFI boundaries, specialized performance constraints, platform requirements, or a uniquely strong library may justify them; familiarity or historical preference alone generally does not.

For native mobile development, Swift is a natural default for iOS and Kotlin for Android when a native application is the right product choice.

Other languages are acceptable when their platform or ecosystem gives a concrete advantage. Prefer the language that best matches the actual product and maintenance environment rather than forcing Rust into a domain where another platform-native choice is clearly stronger.

Use shell only as small glue. Prefer Rust for substantial automation, parsing, validation, or business logic.

## Rust libraries and patterns

These are preferred starting points, not dependencies to add automatically.

- `serde` / `serde_json` for serialization.
- `thiserror` for typed library errors.
- `anyhow` with context at application and operational boundaries.
- `tracing` and `tracing-subscriber` for diagnostics.
- `clap` for command-line interfaces.
- `reqwest` for HTTP clients, normally with Rustls where practical.
- `tokio` for asynchronous runtime needs.
- `axum` for conventional HTTP services.
- `sqlx` for relational database access, preferring compile-time-checked queries when practical.
- Leptos for Rust/WASM browser applications when the Rust-heavy approach is justified.

Keep asynchronous work near I/O and orchestration boundaries. Keep validation, encoding, hashing, state transitions, and other pure logic synchronous when practical.

Do not add `unsafe` code without a compelling, explicitly reviewed need.

## Data and persistence

Prefer relational storage unless the data model genuinely calls for something else.

For experiments, local tools, and simple single-node applications, SQLite is usually the first database to consider. It keeps local development cheap and easy to reproduce.

For conventional multi-user services that need a managed relational database, PostgreSQL is the general default.

For Cloudflare-native applications, D1 is a reasonable SQLite-like hosted option when its current capabilities and limits fit the workload. Verify current platform behavior and limits before committing to it.

Avoid introducing Redis, queues, search clusters, vector databases, or additional persistence systems until the project has a concrete requirement for them.

## Web and deployment

Develop locally first whenever practical. A useful experiment should not require production infrastructure merely to run or test it.

For small public experiments and early products, prefer hosting with low operational burden, predictable cost, and a generous free or inexpensive starting tier.

Cloudflare is the first platform to consider for many such projects:

- Pages for static sites and frontend bundles;
- Workers for lightweight APIs and server-side logic;
- D1 when its relational-storage model fits;
- other Cloudflare services only when a concrete need justifies them.

For Cloudflare Pages, prefer the platform's built-in Git-connected build/deployment workflow when it fits the project. This usually simplifies credential management and gives preview deployments for branches or pull requests without additional CI plumbing. Use custom GitHub Actions or other deployment machinery when there is a concrete requirement the built-in workflow does not satisfy.

Verify current pricing, quotas, runtime limits, and product availability before relying on them; these are operational facts, not permanent architectural truths.

Do not start an experimental product with Kubernetes, a large AWS topology, or a collection of always-on managed services merely because those tools are powerful. AI makes code cheaper; it does not make operational complexity or surprise cloud bills cheap.

Use AWS or another larger cloud platform when requirements actually demand services, control, scale characteristics, networking, compliance, or operational capabilities that the simpler path does not provide.

When deploying an experiment for a non-expert user, explain likely costs, choose conservative limits where the provider supports them, and avoid architectures where an accidental traffic spike can create a disproportionate bill.

## Infrastructure as code

When infrastructure is substantial enough that configuration must be reproduced, reviewed, or maintained over time, prefer an Infrastructure as Code approach rather than relying on manual console changes.

Terraform is the default starting point for provider-managed infrastructure unless the project already has an established Infrastructure as Code tool or another choice has a concrete advantage.

Keep infrastructure definitions in version control and review them alongside application changes when they affect the same behavior. Prefer small, understandable modules and explicit dependencies over building a generalized internal platform prematurely.

Do not introduce Terraform merely to manage a trivial deployment that is already fully described by a platform-native Git integration or a small declarative configuration file. The goal is reproducibility, auditability, and reduced configuration drift—not maximizing the amount of infrastructure code.

Treat Terraform state and provider credentials as sensitive operational data. Use an appropriate remote state backend and locking mechanism when multiple people or automation may apply changes, and never commit secrets or raw state files to source control.

## Containers and CI

Use Docker when it materially improves reproducibility, deployment, or integration testing. Do not make containers mandatory for a program that is simpler to run directly.

Use GitHub Actions as the ordinary first choice for GitHub-hosted project CI unless there is a project-specific reason to use something else or the hosting platform's native Git integration already provides the needed deployment workflow more simply.

Automate formatting, linting/static analysis, tests, and build checks early enough that agents receive fast feedback.

A `justfile` is a reasonable way to expose common repository workflows when commands become numerous or easy to misuse.

## EVM and smart contracts

For new EVM integration code in Rust, prefer Alloy over ethers-based Rust APIs.

Use Foundry for Solidity development and testing unless the existing project has a different established toolchain.

Generate bindings from checked ABIs rather than hand-maintaining overlapping interfaces. Treat chain IDs, addresses, amounts, signatures, and other protocol values as explicit domain types rather than interchangeable strings and integers.

## Choosing something else

A default earns its place by reducing decision cost, not by becoming doctrine.

Use another technology when it provides a material advantage for the actual project. When making a meaningful deviation, capture why so later agents do not repeatedly reopen a settled choice without new evidence.
