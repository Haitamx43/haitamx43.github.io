# MHx1 Cybersecurity Blog

This is a personal cybersecurity blog for **Haitam / MHx1** using the **Chirpy theme for Jekyll**.

Local site:

```text
http://127.0.0.1:4000
```

## Blog Architecture

```text
Blog/
├── _config.yml
├── Gemfile
├── Gemfile.lock
├── index.html
├── README.md
├── .gitignore
├── .nojekyll
├── _posts/
│   ├── 2024-01-15-ssrf-internal-metadata-test-target.md
│   ├── 2024-02-03-tryhackme-linux-easy-room.md
│   ├── 2024-03-10-hackthebox-windows-medium-machine.md
│   └── 2024-04-21-ewptxv3-study-plan.md
├── _tabs/
│   ├── archives.md
│   ├── categories.md
│   ├── tags.md
│   └── about.md
├── assets/
│   ├── css/
│   │   └── jekyll-theme-chirpy.scss
│   └── img/
│       ├── avatar.png
│       └── posts/
├── .github/
│   └── workflows/
│       └── pages-deploy.yml
└── _site/
```

## What Each Part Does

`_config.yml`:
Main Chirpy/Jekyll settings. Blog name, tagline, avatar, email, LinkedIn, timezone, theme mode, pagination, SEO, and build options live here.

`Gemfile`:
Ruby dependencies. It installs Chirpy, Jekyll, and supporting gems.

`index.html`:
Homepage entry file. Chirpy uses `layout: home` to generate the post feed.

`_posts/`:
All blog posts live here. Every post is a Markdown file.

`_tabs/`:
Navigation pages. Your current tabs are Categories, Tags, Archives, and About.

`assets/css/jekyll-theme-chirpy.scss`:
Custom design overrides: colors, avatar circle, link colors, scanline effect, contact icons.

`assets/img/avatar.png`:
Your MHx1 logo/avatar.

`assets/img/posts/`:
Put screenshots, diagrams, and post images here.

`.github/workflows/pages-deploy.yml`:
GitHub Pages deployment workflow.

`_site/`:
Generated output. Do not edit files inside `_site` manually.

## Run the Blog Locally

Open a terminal in:

```text
C:\Users\mriou\Documents\Blog
```

Install dependencies:

```bash
bundle install
```

Start the local server:

```bash
bundle exec jekyll serve
```

Open:

```text
http://127.0.0.1:4000
```

Build the static site:

```bash
bundle exec jekyll build
```

## Add a New Post

Create a new Markdown file inside `_posts`.

The filename must start with a date:

```text
YYYY-MM-DD-your-post-title.md
```

Example:

```text
2026-06-05-my-first-bug-bounty-writeup.md
```

Add this front matter at the top:

```markdown
---
title: "My First Bug Bounty Writeup"
date: 2026-06-05 10:00:00 +0100
categories: [Bug Bounty, HackerOne]
tags: [XSS, Recon, Report Writing]
description: "A short summary shown on the homepage and search results."
toc: true
pin: false
---
```

Write your content below it:

```markdown
## Summary

Short overview of the finding, room, machine, or guide.

## Methodology

Explain your steps.

## Impact

Explain why it matters.

## Remediation

Explain how to fix it.
```

## Post Template: Bug Bounty

```markdown
---
title: "Stored XSS in Profile Bio"
date: 2026-06-05 10:00:00 +0100
categories: [Bug Bounty, HackerOne]
tags: [XSS, Stored XSS, Web AppSec]
description: "A sanitized bug bounty writeup about stored XSS in a profile field."
toc: true
pin: false
---

## Summary

What was vulnerable and where.

## Recon

How you found the feature.

## Exploitation

What payload worked in the authorized test environment.

## Impact

What an attacker could do.

## Remediation

How the team can fix it.
```

## Post Template: TryHackMe

```markdown
---
title: "TryHackMe Room Name Walkthrough"
date: 2026-06-05 10:00:00 +0100
categories: [TryHackMe, Linux]
tags: [Linux, Enumeration, Privilege Escalation]
description: "A TryHackMe room walkthrough focused on enumeration and privilege escalation."
toc: true
pin: false
---

## Enumeration

Commands and discovered services.

## Initial Access

How you got a shell.

## Privilege Escalation

How you moved from user to root/admin.

## Lessons Learned

What the room teaches.
```

## Post Template: HackTheBox

```markdown
---
title: "HackTheBox Machine Name Writeup"
date: 2026-06-05 10:00:00 +0100
categories: [HackTheBox, Windows]
tags: [Windows, SMB, Active Directory]
description: "A HackTheBox machine writeup focused on Windows enumeration."
toc: true
pin: false
---

## Enumeration

Service discovery and notes.

## Foothold

Initial access path.

## Privilege Escalation

Admin path.

## Defensive Notes

How defenders could detect or fix it.
```

## Add Tags

Tags are automatic. Add them in the post front matter:

```markdown
tags: [SSRF, AWS, Cloud Metadata]
```

Then Chirpy automatically adds them to:

```text
/tags/
```

Good tag examples:

```text
XSS
SSRF
SQLi
Recon
Nmap
Burp Suite
Linux
Windows
Active Directory
Privilege Escalation
Report Writing
eWPTXv3
```

Tip: keep spelling consistent. `Active Directory` and `AD` would become two separate tags.

## Add Categories

Categories are automatic. Add them in the post front matter:

```markdown
categories: [Bug Bounty, HackerOne]
```

The first item is the main category. The second item is the subcategory.

Chirpy automatically adds them to:

```text
/categories/
```

Recommended categories for this blog:

```markdown
categories: [Bug Bounty, HackerOne]
categories: [Bug Bounty, Bugcrowd]
categories: [Bug Bounty, Intigriti]
categories: [TryHackMe, Linux]
categories: [TryHackMe, Windows]
categories: [HackTheBox, Linux]
categories: [HackTheBox, Windows]
categories: [Certifications, eWPTXv3]
categories: [Guides, Web AppSec]
```

## Archives

Do not edit archives manually.

Archives are automatic. Chirpy uses the post `date:` field:

```markdown
date: 2026-06-05 10:00:00 +0100
```

The post appears automatically in:

```text
/archives/
```

## Add Images to a Post

Put your image here:

```text
assets/img/posts/
```

Example:

```text
assets/img/posts/ssrf-flow.png
```

Use it in a post:

```markdown
![SSRF redirect flow](/assets/img/posts/ssrf-flow.png)
```

## Add Code Blocks

Use fenced code blocks:

````markdown
```bash
nmap -sC -sV 10.10.10.10
```
````

PowerShell example:

````markdown
```powershell
Get-ADUser -Filter *
```
````

## Useful Post Options

```markdown
pin: true        # keep post near the top
toc: true        # show table of contents
comments: false  # disable comments for this post
math: true       # enable math rendering
mermaid: true    # enable Mermaid diagrams
```

## Edit the About Page

Edit:

```text
_tabs/about.md
```

That file controls the About page text, contact links, skills, tools, and certifications.

## Edit Navigation Order

Each tab in `_tabs/` has an `order` value.

Example:

```markdown
---
title: About
icon: fas fa-user
order: 5
---
```

Lower numbers appear first. Higher numbers appear later.

## Change Colors or Logo Style

Edit:

```text
assets/css/jekyll-theme-chirpy.scss
```

The main accent color currently used is:

```css
#9fd7ff
```

The avatar image is:

```text
assets/img/avatar.png
```

## Common Workflow

1. Create a new post in `_posts`.
2. Add title, date, categories, tags, and description.
3. Write the post.
4. Add images to `assets/img/posts` if needed.
5. Run:

   ```bash
   bundle exec jekyll serve
   ```

6. Open:

   ```text
   http://127.0.0.1:4000
   ```

7. Check Categories, Tags, and Archives.
8. Commit and push when ready.
