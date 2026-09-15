# AGENTS.md — zLawyer newsletters

This repository is the **source of truth** for zLawyer newsletters in two formats:

| File | Channel | Purpose |
|------|---------|---------|
| `NN-<slug>/<slug>.mjml` | Email | Sent as the newsletter email |
| `NN-<slug>/<slug>.md` | Website | Web archive copy (same content intent, article-style prose) |

Sanity / `zLawyerFront` will later ingest the `.md` (or equivalent fields). Until then, both files must stay in sync in this repo.

Every instruction below is a **constraint**, not a suggestion.

---

## Directory layout

```text
01-<slug>/
  <slug>.mjml    # email source
  <slug>.md      # website source (YAML frontmatter + Markdown body)
02-<slug>/
  …
assets/          # shared images if needed
```

- One newsletter = **one folder** named `NN-<slug>` where `NN` is a zero-padded order index (`01`, `02`, …) by publication date (oldest first).
- Inside the folder, file basenames use **`<slug>` only** (no numeric prefix).
- Frontmatter `slug` must equal `<slug>` (no numeric prefix).
- Folder order prefix is for human/agent sorting only; it is not part of the public URL slug.
- Do not leave orphan `.mjml` or `.md` files at the repo root.
- Slugs are ASCII kebab-case only (e.g. `numerotation-factures`, never `numérotation-factures`).

### Renumbering

When inserting a newsletter between existing ones, renumber subsequent folders (`03` → `04`, etc.) so order stays chronological. Prefer appending (`12-…`) when publishing the newest issue.

---

## Mandatory dual format

When **creating** a newsletter:

1. Choose the next order index `NN` (or renumber if inserting).
2. Create folder `NN-<slug>/`.
3. Create `NN-<slug>/<slug>.mjml` (full email).
4. Create `NN-<slug>/<slug>.md` with frontmatter + web body in the same change.
5. Never commit only one of the two files for a new newsletter.

When **updating** a newsletter:

1. If you change the **MJML**, update the **Markdown** in the same change (same facts, CTAs, dates, links, legal lines).
2. If you change the **Markdown**, update the **MJML** in the same change.
3. Do not leave one format outdated relative to the other.
4. Cosmetic-only tweaks that cannot exist in the other format (e.g. Outlook `mso-` hacks in MJML, or web-only heading hierarchy) are allowed **only if** the editorial message stays equivalent — document the exception in the PR/commit body.

---

## Markdown frontmatter (required)

```yaml
---
title: "…"
date: "YYYY-MM-DD"
description: "…"
slug: "<slug>"
---
```

- `slug` must equal the file basename (without `NN-`).
- `description` is used for SEO / listing cards (short).
- Body below the frontmatter is the **website** prose (not a dump of raw MJML).

---

## Content parity rules

Both formats must share the same:

- Title / subject intent (`mj-title` ≈ frontmatter `title`)
- Preview / listing blurb (`mj-preview` ≈ frontmatter `description` when possible)
- Core sections and claims
- Links and CTA URLs
- Dates and product names

Differences that **are** expected:

- MJML = email layout (tables, buttons, logo header, inline styles)
- Markdown = site article style (headings, lists, no email chrome)

Differences that are **not** allowed:

- Different facts, prices, dates, or CTAs
- A section present in one format and missing in the other (unless explicitly marked deprecated in both)

---

## New newsletter checklist

- [ ] Folder `NN-<slug>/` created (correct chronological index)
- [ ] `<slug>.mjml` complete and valid MJML
- [ ] `<slug>.md` with required frontmatter + body
- [ ] Titles / descriptions / links aligned
- [ ] No root-level stray newsletter files

---

## Out of scope here

- Publishing to Sanity or Azure (handled in `zLawyerFront` via `yarn sanity:seed:newsletters` + Studio)
- Sending the email campaign (ESP / manual send)
