# zLawyer newsletters

Source repo for zLawyer newsletters: **email (MJML)** + **website copy (Markdown)** kept in sync.

## Layout

```text
01-<slug>/
  <slug>.mjml   # email
  <slug>.md     # website (frontmatter + body)
02-<slug>/
  …
assets/
AGENTS.md       # rules for humans and coding agents
```

Folders are numbered (`01`, `02`, …) by publication date (oldest first). The public slug is the part **after** the number.

## Rules

See **[AGENTS.md](./AGENTS.md)**:

- Every newsletter has both `.mjml` and `.md`
- Updating one format requires updating the other in the same change

## Website frontmatter example

```yaml
---
title: "…"
date: "YYYY-MM-DD"
description: "…"
slug: "my-newsletter"
---
```
