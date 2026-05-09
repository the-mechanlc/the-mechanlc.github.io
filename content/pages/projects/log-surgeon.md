+++
title = "log-surgeon"
description = "A log parsing and alerting tool that turns structured and unstructured log streams into actionable signals."
date = 2025-08-15
weight = 20

[extra]
github_url = "https://github.com/the-mechanlc/log-surgeon"
demo_url = ""
context = "Built when I got tired of writing the same ad-hoc awk/jq pipelines to extract signal from log noise during incidents. Now runs as a sidecar in production."
status = "active"
+++

`log-surgeon` reads log streams (file, stdin, or Loki API), applies a set of pattern rules defined in a YAML config, and emits alerts to Slack or a webhook when rules match. Rules support regex patterns, rate thresholds, and correlation windows.

The main design goal was zero-dependency deployment: a single static binary with a config file. No Java runtime, no Python virtualenv, no agent framework. It should run anywhere a log file runs.
