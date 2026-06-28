---
title: "TryHackMe Linux Easy Room: Enumeration First"
date: 2024-02-03 10:30:00 +0100
categories: [TryHackMe, Linux]
tags: [Linux, Enumeration, Privilege Escalation, Nmap]
description: "A beginner-friendly Linux room walkthrough focused on service enumeration, web discovery, and a clean privilege escalation checklist."
toc: true
---

> Difficulty: Easy  
> Platform: TryHackMe  
> Points: 30

## Methodology

The room rewarded patience more than payload volume. I started by mapping exposed services, then moved from web discovery into credential reuse and local enumeration.

```bash
nmap -sC -sV -oN scans/initial.txt 10.10.10.10
```

## Web Discovery

Directory discovery found an admin-adjacent path that leaked a backup note. The important lesson was to inspect comments, old extensions, and naming patterns before assuming a vulnerability class.

```bash
ffuf -u http://10.10.10.10/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt
```

## User Access

The backup note led to a low-privilege shell through legitimate credentials. After login, I captured environment details, sudo privileges, writable paths, and scheduled tasks.

## Privilege Escalation

The escalation path was a misconfigured script running with elevated permissions. The fix would be to remove writable access, pin absolute binary paths, and monitor ownership drift in deployment scripts.

## Takeaways

Small Linux rooms are great practice for discipline. Build a repeatable checklist, keep command output organized, and write down why each finding matters before jumping to the next tool.
