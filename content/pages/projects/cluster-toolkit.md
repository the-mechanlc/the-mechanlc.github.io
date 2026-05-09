+++
title = "cluster-toolkit"
description = "A set of scripts and manifests for spinning up opinionated Kubernetes clusters on bare metal and cloud VMs."
date = 2025-11-01
weight = 10

[extra]
github_url = "https://github.com/the-mechanlc/cluster-toolkit"
demo_url = ""
context = "Born out of frustration with setting up the same cluster configuration repeatedly across different environments. Now handles the full lifecycle from bootstrap to teardown."
status = "active"
+++

`cluster-toolkit` started as a collection of shell scripts in a gist. It's now a proper repo with idempotent setup scripts, a sane networking default (Cilium), and a few opinionated choices baked in so I don't have to make the same decisions every time.

It handles: kubeadm bootstrap, CNI setup, ingress controller install, cert-manager, basic monitoring stack, and a teardown script that actually works. Tested on Ubuntu 22.04 and Debian 12.
