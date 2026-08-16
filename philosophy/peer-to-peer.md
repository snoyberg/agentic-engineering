# Peer-to-Peer Agent Guidance

Software development practices have traditionally spread through books, documentation, blog posts, source code, code review, employment, mentorship, and conversation.

AI agents create another mechanism.

An agent can consume a person's accumulated engineering guidance while performing real work. It can also observe where that guidance succeeds, where it creates friction, and where the human repeatedly corrects it.

That makes engineering guidance capable of becoming a living artifact.

## Publish judgment, not just configuration

This repository is not primarily a collection of tool settings.

It attempts to record engineering judgment:

- what tradeoffs we prefer;
- what kinds of bugs we try hardest to prevent;
- which abstractions usually pay for themselves;
- how we review work;
- how much autonomy agents should have;
- how disagreements should be resolved;
- what we have learned from previous projects.

The format is deliberately informal.

Humans and modern AI systems can consume prose, code, examples, links, discussions, commit history, and other repositories directly. We should avoid imposing a schema until experience demonstrates a problem that requires one.

## Collaboration and competition

Healthy engineering ecosystems combine cooperation and disagreement.

We can share basic infrastructure and useful ideas without agreeing on everything.

One person may strongly prefer static typing. Another may optimize for exploratory development.

One person may personally review every commit. Another may intentionally delegate almost all implementation decisions to an agent.

Those differences should be visible rather than normalized away.

Create your own guidance. Reference other people's work. Explain where you disagree. Adopt ideas that work. Send improvements upstream when appropriate.

## Agents as participants

Agents can help this process by noticing patterns that humans would otherwise fail to record.

An agent may notice:

- the same review correction appearing repeatedly;
- a rule that conflicts with actual project practice;
- a useful rule emerging independently in several repositories;
- a recommendation that regularly causes problems;
- a disagreement between two engineering approaches.

Agents should surface these observations and propose changes.

They should not autonomously settle questions of values, risk tolerance, engineering taste, or ownership.

## No central authority

This project does not seek to establish a universal agent coding standard.

Forking is healthy.

Competing recommendations are healthy.

A repository that substantially disagrees with this one may be more valuable to the ecosystem than another repository that simply copies it.

The desired network is one of people and agents exchanging ideas through ordinary public artifacts.

Today Git and GitHub are a convenient substrate.

They do not need to be the final substrate.
