---
title: "eWPTXv3 Study Plan: Advanced Web Exploitation Without Chaos"
date: 2024-04-21 12:00:00 +0100
categories: [Certifications, eWPTXv3]
tags: [eWPTXv3, Web AppSec, Study Plan, Burp Suite]
description: "A practical eWPTXv3 preparation roadmap covering advanced web topics, lab cadence, notes, reporting, and review habits."
toc: true
---

> Certification: eWPTXv3  
> Status: In progress

## Study Goals

The target is not just passing an exam. The goal is to become faster at recognizing exploit chains, cleaner at validating impact, and sharper at writing remediation advice.

## Weekly Structure

| Day | Focus |
| --- | --- |
| Monday | HTTP request smuggling, cache poisoning, parser differentials |
| Tuesday | Advanced XSS, CSP bypasses, DOM sources and sinks |
| Wednesday | SSRF, deserialization, file handling, cloud pivots |
| Thursday | SQL injection edge cases and auth logic |
| Friday | Report writing and replayable evidence |
| Weekend | Full lab chain and retrospective |

## Lab Routine

```bash
mkdir -p notes/{recon,exploitation,evidence,report}
```

Every lab gets the same structure: hypothesis, test, result, impact, and remediation. That makes review sessions useful because weak spots show up as missing evidence, not vague anxiety.

## Tools

Burp Suite is the primary cockpit. I keep `ffuf`, `nuclei`, `httpx`, `jq`, and browser dev tools close, but I avoid turning study sessions into tool collection.

## Exam Readiness Checklist

- I can explain why a bug is exploitable.
- I can reproduce it from a clean session.
- I can show business impact without overreaching.
- I can write a remediation that an engineering team can act on.
