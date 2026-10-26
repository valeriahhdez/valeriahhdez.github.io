---
post: true
date: 2026-07-28
title: Log entry 3 - Choosing a static site generator (but with a plot twist)
author: Valeria Hernandez
description: Third entry in my Engineer the docs series where I share how I came to choose Zensical as my static site generator.
cover: assets/images/covers/logentry3.png
tags:
  - docs as code
  - static site generator
  - engineer the docs
  - open source
---

*This is part of a series where I document building my own docs site from scratch as I go from tech writer to docs engineer, building AI-assisted documentation pipelines.*

I was proud that I'd chosen a static site generator (SSG) in a reasonable amount of time.

I was going to use MkDocs for my site, Material for MkDocs for the look, and a little custom CSS for the illusion of frontend craftsmanship.

I had already done the fun part: tweaked the styles.css file, created the YAML configuration, and made a homepage. The project had crossed that fragile threshold from “I am evaluating tools” to “I am committed to using this SSG”. Then I learned that MkDocs and Material for MkDocs were in the middle of an open-source saga.

Some people watch reality television for the drama. I postpone my “functional adult” responsibilities to read long-form accounts of maintainer disputes, stalled projects, governance problems, and the fate of Python documentation tooling. The tea wasn't merely hot; it had quotes, timelines, and GitHub threads.

The TL;DR is that MkDocs' future had become uncertain, Material for MkDocs had moved into maintenance mode, and the team behind Material had begun building Zensical. If you enjoy a detailed account of how an open-source project can become a character-driven drama, [*The Slow Collapse of MkDocs*](https://fpgmaas.com/blog/collapse-of-mkdocs/) is a must-read.

So, having just customized my MkDocs site, I did the only sensible thing: I started over.

Fortunately, “started over” wasn't as dramatic as it sounds. Migrating to Zensical was surprisingly easy. I pasted in my files, converted the YAML configuration into TOML, and carried on. My custom styles and homepage survived. The site did not need to be rebuilt from the ground up (although I did briefly need to rebuild my sense of momentum).

Having experience with open-source communities myself, I see a lesson here about how much a project's future depends on the health of its community.

Still, I'm very happy with where I landed. Zensical feels modern and powerful, and it lets me maintain the visual direction I had already started shaping. It also lets me move toward a project built by the people whose work made Material so compelling in the first place. I'm that happy with Zensical that I even use it for this blog. 

My static site now has a backstory and a reminder: look behind the scenes of an open-source project and ensure its community is healthy before committing to it.