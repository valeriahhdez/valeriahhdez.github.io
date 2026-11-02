---
post: true
date: 2026-08-20
title: Log entry 5 - Designing an agentic pipeline that can grow
author: Valeria Hernandez
description: Fifth entry in my Engineer the docs series, where I compare architecture options for a modular documentation agent pipeline.
cover: assets/images/covers/logentry5.png
tags:
  - agentic pipeline
  - docs as code
  - quality gates
  - engineer the docs
---

*This is part of a series where I document building my own docs site from scratch as I go from tech writer to docs engineer, building AI-assisted documentation pipelines.*

I had put “build documentation agents” on the roadmap. That was the exciting part. The less exciting, more consequential question was what I meant by *an agent* and how I could build more than one without creating four unrelated scripts held together like a collage.

I planned four agents: drafter, SEO optimizer, alt text generator, and consistency checker. I momentarily dropped the drafter to focus on simpler tasks, so the pipeline needed to check terminology, heading structure, and image descriptions. Those tasks do not share the same judgment rules. But they do share a workflow: discover the right inputs, detect candidates, decide what matters, format the findings, and make them visible to a human reviewer.

That shared shape became the basis for the architecture.

## The first choice: who does what?

I considered three broad approaches.

**Use deterministic checks alone.** Python, parsers, and linters are fast, repeatable, and good at finding exact patterns. They can spot a heading-level skip or a glossary term with the wrong capitalization. But they cannot always tell whether a finding matters in context. A style variation in a heading might be acceptable even if it differs from the glossary.

**Ask an LLM to review whole documents.** That gives the model plenty of context, but also asks it to do the parts computers already handle reliably: find every match and report its location. It can miss occurrences, invent findings, or guess at line numbers. Sending whole documents also means more tokens and less predictable costs.

**Combine deterministic detection with contextual judgment.** This was the option I chose. Code finds the candidates and preserves evidence such as the exact line. An LLM reviews only the candidates that need semantic judgment. That keeps the repeatable work repeatable and uses the model where language is ambiguous.

The short version: tools find things; models help judge what they mean.

## A shared pipeline, with room for different agents

I mapped the common flow as:

```text
Discover → Detect → Validate → Format → Report
```

Discovery is configured explicitly: `agents.yaml` says which agents are enabled and which files they can inspect. Detection belongs to each agent. The consistency checker searches for terminology candidates; the SEO optimizer parses headings; an alt text agent looks for images that need descriptions.

Validation is also agent-specific. Some findings need an LLM to judge context; some need a vision model; some may not need an LLM at all. “Use an LLM because this is an AI project” is not an architecture principle. It is how you end up paying tokens to confirm that a heading starts with `##`.

Each agent gets models that describe its own domain, rather than forcing every result into one generic issue shape. A consistency issue needs a canonical term and the variant found; an SEO issue needs heading context and a suggested fix. A little extra structure is preferable to a universal model with fields that mean different things to different agents.

The shared parts are the plumbing: configuration, document discovery, parsing utilities where tasks overlap, output dispatch, and reporting. 

## A reusable pattern

I wanted the system to be modular so I could easily scale it. New agents should fit the existing system without requiring an architectural redesign. That did not mean every agent should be a copy of the first one.

For example, heading extraction can be a shared parsing utility because more than one agent may need document structure. Output formatting can use a registry: each agent registers its JSON and Markdown formatter, and a shared dispatcher selects the requested format. That keeps report handling consistent while allowing the actual issue fields to differ.

Configuration gives each agent its own sources and options. Explicit, opt-in discovery also avoids scanning documents just because they happen to exist in the repository. 

This was the balance I was after: reuse recurring infrastructure, keep domain logic close to the agent that owns it, and avoid inventing abstractions for hypothetical future agents. 

## CI should surface findings, not hold the site hostage

I also decided the agents should run as non-blocking quality checks. Their reports should be visible in the GitHub Actions summary, with structured JSON saved as an artifact. That gives me both a quick human-readable review and the underlying data for later inspection.

If an agent finds an issue, a person decides what to change. If a model call fails, the report should say what could not be verified. The documentation site should still deploy while I improve the check. This is an editorial support system, not an autonomous editor with a deployment veto.

There is a trade-off: non-blocking checks do not enforce a strict quality gate. For this project, that is deliberate. I want to learn how useful and trustworthy the findings are before making them a condition of deployment. I didn't want to blindly trust these systems. 

## Start with one agent

The architecture file describes a pipeline that could eventually support several agents. I did not want to build all of them at once. This was an opportunity for me to test how easy it was to scale the plumbing.

I decided to build the consistency checker first because its input is simple, the glossary gives me a clear source of truth, and it would exercise the basic pattern without introducing subjective content decisions.

The plan was to build it in stages: 
1. An entry point and mocked flow
1. Configuration and file scanning
1. Model call and report formatting. 

That would let me validate the shape before adding the least predictable part. I was designing for growth, but I have to earn that growth one working piece at a time.

The architecture was not a promise that adding agents would be effortless. It was a way to make the repeated decisions visible: what is shared, what belongs to each agent, where the model is allowed to judge, and how a human sees the result.

Next up: putting this pattern to work with the consistency checker and finding out how much of the tidy architecture survives contact with actual files and actual model responses.
