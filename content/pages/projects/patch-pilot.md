+++
title = "patch-pilot"
description = "An automated dependency patching bot that opens pull requests for security and version updates across repositories."
date = 2026-01-20
weight = 30

[extra]
github_url = "https://github.com/the-mechanlc/patch-pilot"
demo_url = ""
context = "Dependabot is great until you have 30 repos and 200 open dependency PRs with no triage strategy. patch-pilot adds a prioritization layer and auto-merges low-risk patches."
status = "in-progress"
+++

`patch-pilot` runs on a schedule, scans a configured list of GitHub repositories for outdated dependencies, and opens pull requests with a priority score attached. Security patches above a CVSS threshold get auto-merged if CI passes. Everything else goes into a weekly digest.

Currently supports Go modules, npm/yarn, and Python pip. The scoring model weighs CVSS score, dependency depth, and whether the version bump is patch/minor/major.
