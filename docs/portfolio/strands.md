---
portfolio: true
year: 2025
role: technical writer
title: Strands documentation from zero
author: Valeria Hernandez
description: A three-month project to build a documentation website from scratch for a product that had no users yet.
cover: assets/images/covers/strands-cover.png
tags:
  - ux
  - information architecture
  - technical documentation
  - open source
  - docs as code
  - user journeys
---

## Summary

Strands, an online JSON Schema repository, launched with no existing audience, no analytics, and no user research. As the sole technical writer on a contract with Octue, I built its documentation site from scratch: I defined four hypothetical user personas, mapped a documentation journey for each, and used those journeys to drive a content plan and a six-section information architecture. 
I delivered a complete MVP in three months: 9 articles (including 4 use cases and 3 JSON Schema explainers for non-experts), release notes, FAQs, a glossary, support information, and 3 custom diagrams. I benchmarked documentation platforms, chose Theneo, and versioned the content in Git and GitHub.

- Role: Technical writer (contract)
- Client: Octue
- Timeline: January 2025 – March 2025
- Stack: Theneo, Git/GitHub, Figma

## Problem

Strands is an online JSON Schema repository. It had no audience yet, no analytics and no user research, and the docs had to serve four possible personas, from experienced schema authors to people who had never heard of JSON Schema.

## Constraints

Three-month timeline, no user data, a mixed technical audience, and a documentation platform still to be chosen.

## Key decisions

- Personas as hypotheses. With no user data, I drew on Octue's other products to define four personas (goals, pain points, experience level, technical expertise, use case) and treated them as testable assumptions, not facts.
- Journeys turned assumptions into a content plan. I mapped a journey per persona, from discovery to advocacy. For the developer architect, the three biggest struggles (version synchronization, manual distribution, API consistency) became the three challenges that structure their use case, and the outcomes I had mapped became its three solutions.
- What to write: journey questions plus Diataxis. I used the questions from the user journey together with Diataxis to define the content types readers needed.
- How to organize it: by journey, not by content type. The six sections (Getting started, JSON Schema fundamentals, Use cases, Troubleshooting and FAQs, Product updates, Support and feedback) map to the journey stages: the landing page and use cases serve discovery and evaluation, getting started and the fundamentals serve onboarding, and troubleshooting, product updates and support serve adoption and advocacy. A Diataxis-style navigation would have exposed labels that mean little to readers new to JSON Schema and grouped content by type rather than by task. Content types inform the information architecture, but they shouldn't dictate it.
- Use cases as the value proposition. Four use cases show how Strands solves a concrete problem for each user type, rather than listing features.
- A foundations layer for non-experts. Three explainers (key concepts, anatomy of a schema, best practices) keep less technical readers from hitting a wall.
- Visuals only where prose fails. Three Figma diagrams (referencing, validation, schema structure) sit next to the articles that explain those concepts and reinforce them.
- AI-assisted drafting inside a controlled workflow. I built a template for the use case articles and gave it to an AI model together with the persona materials and the Strands value proposition and description to draft each one. I added the Vale linter to the pipeline to enforce Google's style guide. I shared the drafts with Octue's engineers for technical review.
- Platform: benchmark, then partnership. I compared GitBook, Theneo, and ReadMe against four criteria: docs-as-code workflow, open-source support, clear UI and navigation, and aesthetics. Theneo met them, and a partnership between Strands and Theneo, both products launching at the time, made it the practical choice. Content is versioned in Git and GitHub.

## Outcome

An MVP docs site delivered in three months: nine content pieces (four use cases, three foundational explainers, a Get started guide and a glossary), plus release notes, FAQs, support information and three custom diagrams. Strands had no users yet, so there are no usage numbers to report. I left at the end of my contract to join Copado, so the site shipped without a post-launch iteration.

<iframe width="560" height="315" src="https://www.youtube.com/embed/31GR9jgt4i0?si=aRT2gqMWuZhk6IGH" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<p><a class="site-button" href="https://www.figma.com/design/CNEOTEU18m1l0Z6zLavPuQ/Building-a-documentation-website-for-Strands?node-id=0-1&amp;t=SFFrGFQy2XJ8I2PE-1" target="_blank" rel="noopener noreferrer">View the project poster</a></p>

## What I'd do differently

I'd build the means to test the personas in before the handoff: basic analytics and a feedback channel from day one, so whoever continued the project could check the personas against real behavior.

