---
title: "HackTheBox Windows Medium Machine: From SMB Clues to AD Context"
date: 2024-03-10 11:15:00 +0100
categories: [HackTheBox, Windows]
tags: [Windows, SMB, Active Directory, Kerberos]
description: "A Windows machine writeup centered on SMB enumeration, credential hygiene mistakes, and building Active Directory context before exploitation."
toc: true
---

> Difficulty: Medium  
> Platform: HackTheBox  
> OS: Windows

## Initial Enumeration

The machine exposed SMB and a domain-aware authentication surface. I treated the host as part of a broader identity system immediately instead of testing it like an isolated Windows server.

```powershell
nmap -sC -sV -p 53,88,135,139,389,445,464,593,636 10.10.10.20
```

## SMB Clues

Anonymous listing was restricted, but one readable share contained deployment notes with service names and a stale username format. That was enough to shape Kerberos and password-spray decisions safely inside the lab.

## Domain Context

Once a low-privilege account was available, the priority shifted to relationships: groups, SPNs, delegated permissions, local admin paths, and unusual ACLs.

```powershell
net user /domain
net group "Domain Admins" /domain
```

## Privilege Path

The final path came from weak service account hygiene. A recoverable credential unlocked a privileged management group, and from there the machine objective was straightforward.

## Defensive Notes

Rotate service credentials, restrict share contents, audit delegated permissions, and alert on authentication patterns that touch many SPNs or hosts in a short window.
