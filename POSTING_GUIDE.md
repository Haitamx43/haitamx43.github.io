# Blog Posting Guide

Use this guide when creating new posts for Hack The Box, TryHackMe, bug bounty notes, research blogs, or certification guides.

## Where Posts Go

All posts live in:

```text
_posts/
```

Each post must be a Markdown file with this filename format:

```text
YYYY-MM-DD-post-title-slug.md
```

Examples:

```text
2025-02-18-hackthebox-lame-writeup.md
2025-07-04-tryhackme-linux-privesc-notes.md
2026-01-12-ewptxv3-study-roadmap.md
2026-03-20-ssrf-methodology-guide.md
```

The date in the filename controls where the post appears in archives. If the post was solved or written in 2025, use a 2025 filename.

## Basic Post Template

Copy this into a new file inside `_posts/`:

```markdown
---
title: "Post Title Here"
date: 2025-08-14 18:30:00 +0100
categories: [CTF, HackTheBox]
tags: [linux, web, privilege-escalation, nmap]
description: "Short summary shown on the homepage and search results."
toc: true
pin: false
---

## Overview

Write a short introduction here.

## Main Content

Write your notes, commands, screenshots, and explanation here.

## Lessons Learned

- Key lesson one
- Key lesson two
- Key lesson three
```

Keep the filename date and the front matter `date:` on the same day.

Example:

```text
_posts/2025-08-14-hackthebox-lame-writeup.md
```

```markdown
date: 2025-08-14 18:30:00 +0100
```

## Date Rules

Use the real past date if the work happened in the past.

Examples:

```markdown
date: 2025-01-10 20:15:00 +0100
date: 2025-11-03 14:00:00 +0100
date: 2026-06-05 19:45:00 +0100
```

This makes the Archives page show posts under the correct year and month.

Avoid future dates unless you intentionally want the post to be scheduled for later. Future posts may not appear in the local site unless Jekyll is run with future posts enabled.

## Categories

Categories are broad sections. They are created automatically from the `categories:` line in each post.

You do not need to manually create category folders. When you add a post with a new category and rebuild the site, Chirpy creates the category page for you.

Use 1 or 2 categories per post for a clean blog.

Good examples:

```markdown
categories: [CTF, HackTheBox]
categories: [CTF, TryHackMe]
categories: [Bug Bounty, HackerOne]
categories: [Bug Bounty, Bugcrowd]
categories: [Guides, Certifications]
categories: [Research, Active Directory]
categories: [Notes, Linux]
```

Use this structure for your blog:

```text
CTF
Bug Bounty
Guides
Research
Notes

CTF -> HackTheBox
CTF -> TryHackMe
Bug Bounty -> HackerOne
Bug Bounty -> Bugcrowd
Bug Bounty -> Intigriti
Bug Bounty -> YesWeHack
Guides -> Certifications
Guides -> Web Security
Guides -> Active Directory
Notes -> Linux
Notes -> Windows
```

For the structure you asked about:

```text
Bug Bounty
  HackerOne
    Writeups
  Bugcrowd
    Writeups
```

Use this in posts:

```markdown
categories: [Bug Bounty, HackerOne]
tags: [writeup, ssrf, report-writing]
```

And for Bugcrowd:

```markdown
categories: [Bug Bounty, Bugcrowd]
tags: [writeup, idor, report-writing]
```

This keeps the visual category tree clean, and the `writeup` tag separates writeups from methodology, notes, or guides.

If you want a post to be more general, use:

```markdown
categories: [Bug Bounty, Web Security]
tags: [methodology, recon, burp-suite]
```

Important category rules:

- Use capitalized readable names: `Bug Bounty`, `HackTheBox`, `TryHackMe`.
- Reuse the same spelling every time.
- Do not mix `HackTheBox`, `Hack The Box`, and `HTB` as categories. Pick one.
- Keep deeper details in tags, not categories.

## Tags

Tags are specific topics inside the post. They are created automatically from the `tags:` line in each post.

You do not need to manually create tag files. Add the tag to a post, rebuild the site, and the tag appears on the Tags page.

Use lowercase words and hyphens.

Good examples:

```markdown
tags: [linux, nmap, smb, privilege-escalation]
tags: [windows, active-directory, kerberoasting, bloodhound]
tags: [web, xss, ssrf, idor, burp-suite]
tags: [ewptxv3, study-plan, web-security, methodology]
tags: [tryhackme, enumeration, reverse-shell, privesc]
```

Recommended tags for your blog:

```text
writeup
methodology
recon
enumeration
report-writing
bug-bounty
hackerone
bugcrowd
hackthebox
tryhackme
linux
windows
active-directory
web
api
ssrf
xss
idor
sqli
csrf
rce
lfi
file-upload
authentication
authorization
burp-suite
nmap
ffuf
gobuster
smb
kerberos
privilege-escalation
reverse-shell
cloud-metadata
aws
ewptxv3
oscp
pnpt
cpts
study-plan
checklist
```

Keep tag names consistent. For example, always use:

```text
privilege-escalation
```

Do not sometimes use:

```text
priv-esc
privesc
privilege escalation
```

Consistent tags make the Tags page look cleaner.

Use tags like filters. A Hack The Box post can have:

```markdown
categories: [CTF, HackTheBox]
tags: [writeup, linux, nmap, web, privilege-escalation]
```

A HackerOne writeup can have:

```markdown
categories: [Bug Bounty, HackerOne]
tags: [writeup, ssrf, cloud-metadata, burp-suite, report-writing]
```

A certification guide can have:

```markdown
categories: [Guides, Certifications]
tags: [ewptxv3, study-plan, web-security, burp-suite]
```

To rename a tag:

1. Search every post in `_posts/`.
2. Replace the old tag with the new tag.
3. Run `bundle exec jekyll build`.
4. Check the Tags page locally.

To remove a tag:

1. Remove it from every post that uses it.
2. Rebuild the site.
3. The tag disappears when no post uses it anymore.

## Hack The Box Writeup Template

Filename example:

```text
_posts/2025-04-22-hackthebox-machine-name-writeup.md
```

Post template:

````markdown
---
title: "Hack The Box: Machine Name Writeup"
date: 2025-04-22 21:00:00 +0100
categories: [CTF, HackTheBox]
tags: [linux, nmap, web, reverse-shell, privilege-escalation]
description: "Walkthrough for Machine Name from Hack The Box, covering recon, exploitation, and privilege escalation."
toc: true
pin: false
---

## Overview

Machine Name is a Linux/Windows machine from Hack The Box. This writeup covers enumeration, initial access, and privilege escalation.

## Recon

```bash
nmap -sC -sV -oN nmap.txt 10.10.10.10
```

Write what ports and services you found.

## Enumeration

Explain web directories, SMB shares, users, credentials, files, or services discovered.

## Initial Access

Explain how you got the first shell or foothold.

## Privilege Escalation

Explain how you moved from a low-privileged user to root or administrator.

## Proof

Mention user/root flags only if allowed by the platform rules.

## Lessons Learned

- What was the main vulnerability?
- What tool or technique helped most?
- What would you check faster next time?
````

## TryHackMe Writeup Template

Filename example:

```text
_posts/2025-06-09-tryhackme-room-name-writeup.md
```

Post template:

````markdown
---
title: "TryHackMe: Room Name Writeup"
date: 2025-06-09 17:30:00 +0100
categories: [CTF, TryHackMe]
tags: [linux, enumeration, web, privesc]
description: "Notes and walkthrough for the Room Name room on TryHackMe."
toc: true
pin: false
---

## Overview

Short summary of the room, difficulty, and main skills practiced.

## Recon

```bash
nmap -sC -sV -oN nmap.txt TARGET_IP
```

## Enumeration

Write what you found and how you found it.

## Exploitation

Explain the vulnerability or technique used.

## Privilege Escalation

Explain the path to root/admin.

## Key Takeaways

- Takeaway one
- Takeaway two
- Takeaway three
````

## Bug Bounty Or Web Security Post Template

Filename example:

```text
_posts/2026-02-03-ssrf-methodology-guide.md
```

Post template:

````markdown
---
title: "SSRF Methodology Guide"
date: 2026-02-03 16:00:00 +0100
categories: [Bug Bounty, Web Security]
tags: [ssrf, recon, burp-suite, methodology, web]
description: "A practical SSRF testing methodology for bug bounty and web application security."
toc: true
pin: false
---

## Overview

Explain the goal of the guide.

## When To Test

List features where this bug class appears.

## Testing Methodology

Step-by-step approach.

## Payload Examples

```text
http://127.0.0.1/
http://localhost/
http://169.254.169.254/
```

## Impact

Explain possible impact clearly.

## Mitigation

Explain how developers can fix or reduce the risk.

## Checklist

- Check URL fetchers
- Check file import features
- Check webhook integrations
- Check image upload by URL
````

## Certification Guide Template

Filename example:

```text
_posts/2025-12-15-ewptxv3-study-plan.md
```

Post template:

```markdown
---
title: "eWPTXv3 Study Plan"
date: 2025-12-15 12:00:00 +0100
categories: [Guides, Certifications]
tags: [ewptxv3, web-security, study-plan, burp-suite, methodology]
description: "A structured study plan for preparing for eWPTXv3."
toc: true
pin: false
---

## Overview

Explain who the guide is for and what it covers.

## Prerequisites

- Web fundamentals
- Burp Suite
- Basic scripting
- Common vulnerabilities

## Study Roadmap

### Week 1

Topic and goals.

### Week 2

Topic and goals.

### Week 3

Topic and goals.

## Practice Labs

List labs, rooms, or machines to practice.

## Notes

Add personal notes, mistakes, and lessons learned.

## Final Checklist

- Review methodology
- Practice report writing
- Practice chained vulnerabilities
- Review payloads and bypasses
```

## Images And Screenshots

Put screenshots in:

```text
assets/img/posts/
```

Example image path:

```text
assets/img/posts/hackthebox-machine-name-nmap.png
```

Use it in a post like this:

```markdown
![Nmap scan result](/assets/img/posts/hackthebox-machine-name-nmap.png)
```

Good image naming:

```text
machine-name-nmap.png
machine-name-login-page.png
machine-name-reverse-shell.png
ewptxv3-roadmap.png
ssrf-burp-request.png
```

## Code Blocks

Use code fences for commands:

````markdown
```bash
nmap -sC -sV -oN nmap.txt 10.10.10.10
```
````

Use `text` for raw output:

````markdown
```text
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
```
````

Use `python` for scripts:

````markdown
```python
import requests

url = "http://target.local"
r = requests.get(url)
print(r.status_code)
```
````

## Pinning Posts

Use this if you want a post to stay near the top:

```markdown
pin: true
```

Normal posts should use:

```markdown
pin: false
```

## Table Of Contents

Use this to show a table of contents:

```markdown
toc: true
```

For very short posts, you can disable it:

```markdown
toc: false
```

## Clean Post Checklist

Before publishing, check:

- Filename starts with the correct date.
- Front matter `date:` matches the filename date.
- `title:` is clean and readable.
- `description:` summarizes the post in one sentence.
- `categories:` are broad and consistent.
- `tags:` are lowercase and reusable.
- Images are placed in `assets/img/posts/`.
- Code blocks use the correct language.
- The post does not include secrets, private IPs you should not share, or platform-prohibited flags.

## Verify Locally

Build the blog:

```powershell
$env:BUNDLE_USER_HOME='C:\Users\mriou\Documents\Blog\.bundle-user'
bundle exec jekyll build
```

Run the blog:

```powershell
$env:BUNDLE_USER_HOME='C:\Users\mriou\Documents\Blog\.bundle-user'
bundle exec jekyll serve
```

Open:

```text
http://127.0.0.1:4000/
```

Then check:

- Homepage shows the post.
- Archives page shows it under the correct year and month.
- Categories page includes the category.
- Tags page includes the tags.
- The post page opens correctly.
- Images load correctly.

## Full Blog Management

Use these files and folders when managing the whole blog.

```text
_posts/                         Your blog posts
assets/img/posts/               Screenshots and post images
assets/img/                     Avatar, logo, and general images
_tabs/                          Top navigation tabs
assets/css/jekyll-theme-chirpy.scss  Custom design changes
_config.yml                     Main blog settings
POSTING_GUIDE.md                This guide
```

Important settings in `_config.yml`:

```yaml
title: MHx1
tagline: Offensive Security | Bug Bounty | CTF Player
url: "https://haitamx43.github.io"
baseurl: "/Blog"
avatar: /assets/img/avatar-mhx1-profile.png
```

Use this rule for `baseurl`:

```text
Local preview at http://127.0.0.1:4000/Blog/ -> baseurl: "/Blog"
Live root site at https://haitamx43.github.io/ -> baseurl: ""
Live project site at https://haitamx43.github.io/Blog/ -> baseurl: "/Blog"
```

Right now, your local preview is using:

```yaml
baseurl: "/Blog"
```

If you publish to the root repository `haitamx43.github.io` and want the site at `https://haitamx43.github.io/`, change it before publishing to:

```yaml
url: "https://haitamx43.github.io"
baseurl: ""
```

After changing `baseurl`, stop the Jekyll server with `Ctrl + C`, run it again, and open the matching URL.

### Create A New Post

1. Create a new file in `_posts/`.
2. Name it like `YYYY-MM-DD-title-slug.md`.
3. Add front matter at the top.
4. Add your Markdown content below the front matter.
5. Add images to `assets/img/posts/`.
6. Run `bundle exec jekyll build`.
7. Preview the site at the URL that matches `baseurl`. Right now that is `http://127.0.0.1:4000/Blog/`.

Example:

```text
_posts/2025-09-17-hackerone-ssrf-writeup.md
```

```markdown
---
title: "HackerOne: SSRF Writeup"
date: 2025-09-17 19:30:00 +0100
categories: [Bug Bounty, HackerOne]
tags: [writeup, ssrf, cloud-metadata, burp-suite, report-writing]
description: "A HackerOne SSRF writeup covering discovery, impact, and report structure."
toc: true
pin: false
---

## Overview

Write the summary here.
```

### Create Categories

Add categories in the front matter:

```markdown
categories: [Bug Bounty, HackerOne]
```

That creates or updates:

```text
Bug Bounty
HackerOne
```

Use these examples:

```markdown
categories: [Bug Bounty, HackerOne]
categories: [Bug Bounty, Bugcrowd]
categories: [CTF, HackTheBox]
categories: [CTF, TryHackMe]
categories: [Guides, Certifications]
categories: [Notes, Linux]
categories: [Notes, Windows]
```

### Create Tags

Add tags in the front matter:

```markdown
tags: [writeup, ssrf, burp-suite, report-writing]
```

That creates or updates those tag pages automatically.

Use tags for:

- Vulnerability types: `ssrf`, `xss`, `idor`, `sqli`, `rce`.
- Tools: `burp-suite`, `nmap`, `ffuf`, `gobuster`.
- Platforms: `hackthebox`, `tryhackme`, `hackerone`, `bugcrowd`.
- Systems: `linux`, `windows`, `active-directory`, `aws`.
- Post type: `writeup`, `methodology`, `checklist`, `study-plan`.

### Order Categories

Chirpy orders category and tag pages automatically. You control the structure by consistently using the first and second category.

Good:

```markdown
categories: [Bug Bounty, HackerOne]
categories: [Bug Bounty, Bugcrowd]
```

Avoid:

```markdown
categories: [HackerOne, Bug Bounty]
categories: [Bugcrowd, Bug Bounty]
```

For your preferred order, use:

```text
Bug Bounty -> HackerOne
Bug Bounty -> Bugcrowd
Bug Bounty -> Intigriti
Bug Bounty -> YesWeHack
CTF -> HackTheBox
CTF -> TryHackMe
Guides -> Certifications
Notes -> Linux
Notes -> Windows
```

### Edit Tabs

Tabs live in:

```text
_tabs/
```

Each tab file has front matter. Example:

```markdown
---
layout: page
title: About
icon: fas fa-info-circle
order: 4
---
```

Change `order:` to move a tab left or right in the navigation.

### Edit The Avatar Or Logo

Images live in:

```text
assets/img/
```

The current avatar path is controlled in `_config.yml`:

```yaml
avatar: /assets/img/avatar-mhx1-profile.png
```

If you replace the avatar, keep the image name the same or update `_config.yml`.

### Edit The Design

Custom CSS lives in:

```text
assets/css/jekyll-theme-chirpy.scss
```

After changing CSS, run:

```powershell
bundle exec jekyll build
```

Then hard refresh the browser:

```text
Ctrl + F5
```

### Publish With GitHub Desktop

Before publishing:

1. Run `bundle exec jekyll build`.
2. Open `http://127.0.0.1:4000/`.
3. Check homepage, posts, archives, categories, tags, and tabs.
4. Make sure no private notes, tokens, private IPs, or forbidden flags are in posts.
5. Open GitHub Desktop.
6. Select the blog repository.
7. Review changed files.
8. Write a clear commit message, for example `Update blog posts and guide`.
9. Click `Commit to main`.
10. Click `Push origin`.
11. Wait for GitHub Pages to finish building.
12. Open `https://haitamx43.github.io/`.
13. Use `Ctrl + F5` if the old style appears.

### GitHub Pages Settings

This repository uses the workflow file:

```text
.github/workflows/pages-deploy.yml
```

Because of that, use this GitHub Pages setting:

```text
Settings -> Pages -> Source -> GitHub Actions
```

Do not use `Deploy from a branch` unless you remove the workflow and want GitHub to build the site directly from the branch.

After pushing from GitHub Desktop:

1. Open the repository on GitHub.
2. Click `Actions`.
3. Open the latest `Deploy Jekyll Site` run.
4. Wait until both jobs are green:
   - `build`
   - `deploy`
5. Then open `https://haitamx43.github.io/`.

If the online site looks broken:

- If you see `404 There isn't a GitHub Pages site here`, Pages is not deployed yet. Check `Settings -> Pages` and set the source to `GitHub Actions`.
- If the latest action is red, open it and read the failed step.
- Check `_config.yml` has the correct `baseurl` for the URL you are using.
- Check image links start with `/assets/...` in posts.
- Check the browser is opened at `https://haitamx43.github.io/`.
- Wait a few minutes for GitHub Pages cache.
- Hard refresh with `Ctrl + F5`.
- Rebuild locally and fix any error before pushing again.

## Example Complete Post

Filename:

```text
_posts/2025-08-14-hackthebox-example-machine-writeup.md
```

Content:

````markdown
---
title: "Hack The Box: Example Machine Writeup"
date: 2025-08-14 18:30:00 +0100
categories: [CTF, HackTheBox]
tags: [linux, nmap, web, reverse-shell, privilege-escalation]
description: "A practical walkthrough of Example Machine from Hack The Box."
toc: true
pin: false
---

## Overview

Example Machine is a Linux box focused on web enumeration and basic privilege escalation.

## Recon

```bash
nmap -sC -sV -oN nmap.txt 10.10.10.10
```

Important findings:

```text
22/tcp open ssh
80/tcp open http
```

## Enumeration

The web server exposed a login page and several interesting directories.

```bash
ffuf -u http://10.10.10.10/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

## Initial Access

Explain the vulnerability and how you used it to get a shell.

## Privilege Escalation

Explain the privesc path clearly.

## Lessons Learned

- Recheck web directories after finding credentials.
- Always inspect service versions.
- Keep notes organized during enumeration.
````
