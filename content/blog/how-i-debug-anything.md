+++
title = "How I Debug Anything"
description = "A practical debugging philosophy built from years of 2am incidents and confusing production failures."
date = 2026-05-01

[taxonomies]
tags = ["debugging", "engineering", "process"]
+++

I've been debugging production systems for long enough to have developed a philosophy about it. Not a formal methodology — more like a set of instincts that have saved me time across enough different situations that I now trust them.

The philosophy fits in one sentence: **debugging is the process of narrowing the space of possible causes until only one remains.**

Everything else follows from that.

## Start with what you know, not what you think

The first instinct when something breaks is to reach for the most likely explanation. "It's probably the database." "The deploy must have changed something." "This looks like a race condition." These hypotheses feel useful but they're often wrong, and worse, they bias your observation.

Before I form a hypothesis, I look at data. What is the system actually doing? Not what should it be doing, not what was it doing yesterday — what is it doing right now? Logs, metrics, traces, `strace` output, whatever the system produces. I read it without a filter for at least five minutes before I let myself theorize.

This sounds slow. It saves time.

## Bisect, always bisect

The most powerful debugging technique I know is binary search on the problem space. When something is broken, find the midpoint between "definitely working" and "definitely broken" and test it. If that's broken, your bug is in the first half. If it's working, your bug is in the second half. Repeat.

This works for code (git bisect), for configuration (revert half the changes), for infrastructure (test with half the nodes), for data (does it fail on the first half of the input?). Almost every debugging scenario has a bisectable structure if you look for it.

The failure mode here is not finding the midpoint — guessing at the cause and jumping straight to a fix. That's not debugging, that's gambling with extra steps.

## Reproduce it before you fix it

I will not fix a bug I cannot reproduce. This is a rule I broke early in my career and stopped breaking after I "fixed" the same incident three times and caused a fourth. If I can't reliably make the problem happen in a controlled setting, I don't understand the problem, and a fix I don't understand will fail in ways I didn't anticipate.

Getting a reproduction case is sometimes most of the work. That's fine. A reliable reproduction case is already most of the value — it's a test that didn't exist before, documentation of the failure mode, and a clear target for verification.

## Read the error message

This is embarrassing advice to give and I give it anyway because I have to give it to myself regularly: read the full error message before you do anything else. Not the first line. Not the last line you remember from last time. The whole thing.

Error messages in well-maintained systems are written by people who knew exactly what went wrong. They contain the filename, the line number, the specific constraint that was violated, the value that was unexpected. Half the time, the fix is in the error message and the only thing standing between the error and the fix is three minutes of not-reading.

## Know when to ask for help

There's a threshold I've learned to notice: if I've been looking at the same problem for more than 45 minutes without making progress — not debugging-slowly, but genuinely not narrowing the space — I explain the problem to someone else. This can be a colleague. It can also be a rubber duck, a blank document, or the start of a Stack Overflow question I'll delete once I've answered it myself.

The act of articulating the problem forces a reorganization of what you know. Nine times out of ten, I figure out the issue while writing the question. The tenth time, the person I ask sees something I couldn't see because I was too close to it.

Debugging is a skill, not a talent. It gets better with deliberate practice and honest self-assessment of where you went wrong. Keep a failure log. Read it occasionally. You'll find the same patterns recurring, and then you can fix those too.
