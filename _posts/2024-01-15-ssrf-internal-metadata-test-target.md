---
title: "SSRF to Internal Metadata Access on a Test Target"
date: 2024-01-15 09:00:00 +0100
categories: [Bug Bounty, HackerOne]
tags: [SSRF, Cloud Metadata, AWS, Report Writing]
description: "A sanitized bug bounty case study showing how a server-side URL fetcher reached internal cloud metadata in an authorized test environment."
pin: true
toc: true
---

> Severity: Critical  
> Reward: $500  
> Scope: Authorized test target

## Scope and Setup

This report describes an authorized test target with a document preview feature that accepted remote URLs. The application fetched the URL server-side, rendered a thumbnail, and stored a copy for later review.

```text
focus: request brokers, previewers, webhook testers, PDF generators, importers
rule: only test systems where you have explicit permission
```

## Discovery

The first signal was not a direct data leak. It was timing. Requests to controlled infrastructure arrived from a cloud egress address, not from my browser.

```bash
curl -i "https://example.test/import?url=https://collaborator.example/mhx1"
```

The target blocked common private ranges, but normalization differed between validation and the final fetcher. That gap allowed a controlled redirect to an internal metadata endpoint in the lab account.

## Impact

The test environment exposed metadata that could identify the instance role and region. The report avoided pulling secrets and stopped after proving access to non-sensitive metadata paths.

## Remediation

- Resolve and validate the final destination after every redirect.
- Block link-local, loopback, private, and cloud metadata ranges at the network layer.
- Use an allowlist for expected business integrations.
- Strip response bodies from failed fetch previews and log only safe metadata.

## Reporting Notes

The most useful evidence was a minimal request chain, a diagram of the redirect flow, and proof that the response came from an internal-only service. I included exact timestamps so the program team could correlate logs quickly.
