+++
title = "Now"
description = "What the mechanic is currently working on, reading, and thinking about."
date = 2026-05-09
template = "now.html"
+++

## Working on

- `patch-pilot` — the scoring model for dependency prioritization needs rework after I found edge cases where patch-level bumps in core networking libs were getting scored too low
- This site — finally making it public after three months of "I'll add one more thing first"
- A write-up on the incident from last month where a misconfigured readiness probe caused a cascading failure across three services; still collecting notes

## Reading

- *The Pragmatic Programmer* for the third time — different things land at different points in a career
- The Cilium documentation, specifically the eBPF datapath section, because I still don't fully trust what I haven't read

## Paying attention to

The gap between what observability tooling promises and what it actually delivers in a four-person ops team with real budget constraints. Not everything needs a distributed trace; sometimes you just need a log that says what actually happened.

Also: whether `patch-pilot` should grow a web UI or stay a pure CLI tool. Leaning toward CLI-only and a good JSON output format that other tools can consume.

## Not working on

Rewrites. I have three half-finished rewrites of old projects that I keep convincing myself are "almost done." They're not. Freezing them until the active projects ship.

---

*Last updated: May 2026*
