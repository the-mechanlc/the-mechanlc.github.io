+++
title = "Tools of the Trade"
description = "The tools the mechanic actually reaches for — not the fashionable ones, the ones that work."
date = 2026-04-15

[taxonomies]
tags = ["tools", "cli", "workflow"]
+++

Every mechanic has a short list of tools they trust completely. Not the ones they mention in job interviews or write on their CV — the ones they actually reach for when something is broken and they need to think clearly.

Here's mine.

## `ripgrep` — search that doesn't slow you down

I switched from `grep` to `ripgrep` a few years ago and the only thing I regret is not switching sooner. The defaults are right: respects `.gitignore`, searches recursively, fast enough that I never sit waiting. I use it probably fifty times a day. If you're still using `grep -r`, give it a week with `rg` and you won't go back.

The flag I use most: `-l` for "just give me the filenames". The second most: `-A 5` for context lines after a match. The third: `--type` to filter by language.

## `jq` — the Swiss Army knife for JSON

I resisted `jq` for embarrassingly long because the syntax looked alien. Then I spent a weekend with the docs and came out the other side able to parse any API response or log format in thirty seconds. It's become reflexive. `curl | jq .` is how I start almost every API investigation.

The pattern I use constantly: `jq '.[] | select(.status == "failed") | {id, message}'`. Filter, reshape, done. No Python script, no temporary file, no context switch.

## `tmux` — sessions that outlive your SSH connection

If you're SSHing into remote machines without a session manager, you're one dropped connection away from losing your work. `tmux` is the answer I've settled on. I keep a consistent layout: main pane for the work, smaller pane below for logs, status bar showing host and current directory.

The thing I tell everyone new to `tmux`: learn `prefix + [` for copy mode first. That alone is worth the learning curve.

## `strace` / `lsof` — when you need to see what's actually happening

Most debugging happens at the application level. When it doesn't — when a process is hanging or doing something unexpected at the system level — `strace` and `lsof` are the tools that cut through the mystery. `strace -p <pid>` to attach to a running process and watch its system calls. `lsof -p <pid>` to see what files it has open. Between these two, you can usually figure out why something is stuck.

## `fzf` — fuzzy finding everything

Shell history search with `fzf` is one of those productivity improvements that sounds minor and turns out to be significant. I have it wired up to `ctrl-r` for history, `ctrl-t` for file finding, and `alt-c` for directory jumping. The killer feature is piping any list into it: `git branch | fzf` to check out branches, `docker ps | fzf` to get a container ID.

## A note on fashionable tools

Every few months there's a new tool that's supposed to replace one of the above. Some of them are genuinely better. Most of them are laterally different at best. My test: if I can't use it fluently after an hour, it has to earn its place. The tools above all passed that test and kept delivering years later.

The honest truth about tooling is that mastery matters more than selection. A mechanic who knows their wrench beats one who's still figuring out which socket set to buy.
