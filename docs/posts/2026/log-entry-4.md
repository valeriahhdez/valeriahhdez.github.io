---
post: true
date: 2026-08-10
title: Log entry 4 - Building a documentation roadmap
author: Valeria Hernandez
description: Fourth entry in my Engineer the docs series where I use a documentation user journey to build a documentation roadmap.
cover: assets/images/covers/logentry4.png
tags:
  - docs as code
  - information architecture
  - documentation roadmap
  - engineer the docs
---

*This is part four of a series where I document building my own docs site from scratch as I go from tech writer to docs engineer, building AI-assisted documentation pipelines.*

With the pipeline architecture, branding, and static site generator decisions locked, it was time to build a roadmap for the documentation.

## Starting from questions

This is not the first time I've built a documentation website from scratch. I've written an [article](/posts/2025/documentation-user-journey) about how I use user questions to create a documentation roadmap. I call this approach the "documentation user journey."

In short, the documentation user journey maps users' questions about a product to their respective stage in the product journey. If you don't know what questions users have about your product, you can start with the universal questions every user asks when they encounter something new:

- What's this?
- What does it do?
- What problem does it solve?
- Is it compatible with my current workflows?
- How do I get started?
- How do I do X?
- Why is it not working?

Then, brainstorm the articles that answer those questions. For example, the first four questions could be answered with a product landing page and an overview. The fifth needs a get started guide, and so on.

This time, though, there's no product. *Engineer the docs* is about transitioning from technical writing to owning the systems that produce and maintain documentation (AI included), so the learning curve is the product itself. The good news is that I'm the main user persona, so I can tap into my own questions about the topic. The caveat is that a persona of one has blind spots, so I'll validate these choices when analytics and reader feedback are in place.

And that's what I did. I dumped every question I had about docs engineering, docs as code, agentic systems, observability, measuring documentation, information architecture, linters, agent-friendly documentation, and more.

## Deciding what makes the MVP

I have far more questions than an MVP can hold, and my inner backlog goblin wants all of them at once. My criterion was to include what lays the foundation to scale later. A useful test for "foundation" is a dependency check: could a later article be written without this one? If not, it's foundation.

Here's what passed the test:

- **Getting started:** the basics of docs as code, plus building and deploying. I need everyone finding my website to understand what I mean when I use the terms "docs engineer," "docs as code," and "docops." A docs site nobody can visit is just a hobby, so deploying belongs here too.
- **Quality gates:** consistency and quality checks (linters) that run without me nagging myself.
- **Agentic workflows:** some repetitive tasks can be automated with AI agents. Knowing how to build an architecture you can easily plug agents into is key.
- **Content structure:** a good-enough information architecture (IA) is the foundation of everything else.
- **Agent-friendly documentation:** agents increasingly sit between your docs and your readers.

Everything else goes into the "later" pile, which, as with every documentation backlog, grows like [the blob](https://en.wikipedia.org/wiki/The_Blob_%281988_film%29).

## From a journey to topics

Choosing the IA is the tricky part. I've been reading about IA for years, and I still occasionally rename a category three times before lunch. IA seems to me the easiest part to get wrong. Even if your documentation answers your users' questions, if the way you organize the articles or the labels you choose for categories is off, your readers won't find those answers. Often there isn't a single correct IA, and you just have to keep iterating on it. I've come to accept that, and now my only concern is avoiding the *wrong* IA.

The best protection against the wrong IA is knowing how your readers will look for things. The user journey helped me generate the questions, but it doesn't dictate how to organize the answers. A journey-based structure works when readers move through stages with a product: evaluating it, installing it, using it, troubleshooting it. My readers (a very exclusive group of one, plus whoever else is curious) don't do that. They arrive with a topic they want to dive into.

So the questions stay as the raw material, and the topics become the structure. I expect the navigation to be more of a "what do you want to learn today?" type. Every topic will need its own beginner-to-master-of-the-universe path embedded, and that's where content types come in: within each topic, concepts explain, tutorials teach, and how-tos get things done.

To check this, I asked myself how I'd expect to find things if I landed on a site like this. I'd look for the documentation process I want to address. If I want to keep my docs consistent and high quality, I'd look for "Quality gates." When I have to make docs easy for agents to consume, I'd expect to find "everything you wanted to know about agent-friendly documentation, but were afraid to ask" in a single content bucket.

The meeting was short, and me, myself, and I agreed on organizing the documentation by topics.

## From questions to articles

I didn't stop at questions and categories. Following the same method from my user journey article, I also brainstormed the articles that should answer those questions. Those articles are the MVP set: each card in the diagram below is one planned article, labeled by content type (concept, tutorial, or how-to). Emphasis on "planned," as in "let's see if they stick."

![Diagram of the Engineer the Docs MVP documentation structure: five categories (Getting started, Quality gates, Agentic workflows, Content structure, and Agent-friendly documentation), each with its planned articles listed beneath it.](../../assets/images/figures/docs-mvp.png){: .rounded }

For readers using a screen reader, here's the same structure as a list:

- **Getting started**
    - Concept: Docs as code, docs engineering, and docops: what's the difference?
    - Tutorial: Set up a docs-as-code project and run it locally
    - How-to: Deploy your site to GitHub Pages
- **Quality gates**
    - How-to: Set up a GitHub Actions workflow with quality gates
- **Agentic workflows**
    - Concept: Agent architecture decisions
    - Tutorial: Build a modular docs-agent framework
- **Content structure**
    - Concept: How to think about information architecture for a docs site
    - How-to: Build a content roadmap for your project
- **Agent-friendly documentation**
    - Concept: What agent-friendly documentation is
    - How-to: Make a Zensical site agent-friendly and verify it with afdocs

Quality gates is the thinnest category for now, with a single article. I'm fine with that for an MVP, and it gives the category room to grow.

Next up: adding linters, building documentation agents, and deploying the site.
