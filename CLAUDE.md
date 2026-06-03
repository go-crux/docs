# crux/docs/ — Technical Context

The Crux help centre at docs.gocrux.io. Inherits master context from
`<CRUX>/CLAUDE.md` and platform context from `<CRUX>/crux/CLAUDE.md`.

GitHub repo: `go-crux/docs`. Content is for founders, heads of growth and CFOs,
not engineers.

This file holds the full writing conventions, component patterns, Diataxis
classification and branch/PR workflow for the help centre. Read it before
creating pages, editing content, changing navigation or running a docs audit.

---

## Working relationship

- You can push back on ideas, this leads to better documentation. Do not be a
  sycophant.
- ALWAYS ask for clarification rather than making assumptions.
- NEVER lie, guess, or make up content. If you are unsure whether a feature
  behaves as written, check the source (dbt models, the analyst bot, the
  website) or ask.
- Never create new top-level tabs or folders without user approval. Propose the
  structure first.
- For bulk audits, report findings first and get approval before applying fixes.

---

## Project context

- **Mintlify** — docs framework. Format is `.mdx` (Markdown + JSX components)
  with YAML frontmatter. Configuration, navigation, theme, navbar and footer all
  live in `docs.json` (theme `mint`).
- **GitHub** (`go-crux/docs`) — pushes to `main` trigger automatic deployment via
  the Mintlify GitHub app. Each PR gets a Mintlify preview deployment.
- **Local preview:** `npm i -g mint`, then `mint dev` from the repo root (where
  `docs.json` lives) → `http://localhost:3000`. Run `mint broken-links` to
  validate internal links before opening a PR. There is no other build step.

---

## Content strategy

- Document just enough for user success, not too much, not too little.
- Prioritise accuracy and usability. Make content evergreen where possible.
- Before writing, search existing pages to avoid duplication and read 2-3 pages
  in the same section to match style and depth.
- Start with the smallest reasonable change.
- Classify new pages with the Diataxis framework to pick the right shape:
  - **Tutorial** (learning) — "Getting started with...", guided steps.
  - **How-to guide** (problem) — action verb, prerequisites then numbered steps.
  - **Reference** (information) — noun title, tables and lists, no narrative.
  - **Explanation** (understanding) — "How ... works", problem-first concept.

---

## Structure

```
crux/docs/
├── docs.json              Mintlify config: tabs → groups → pages, theme, navbar
├── index.mdx              Landing page
├── product-updates.mdx    Changelog, surfaced as a global anchor
├── overview/              "Overview" tab
├── analysis-framework/    "The Analysis Mindset" tab
├── dashboard-suite/       "Dashboard Suite" tab (1:1 with dbt mart subfolders)
├── health-metrics/        nested under Dashboard Suite
├── attribution/           "Attribution" tab
├── snippets/              reusable MDX snippets
├── video-scripts/         source scripts for Loom report walkthroughs (not published)
├── logo/ images/          brand assets
└── favicon.png
```

Tabs (top-level): **Overview**, **The Analysis Mindset**, **Dashboard Suite**,
**Attribution**. Persistent **Product Updates** link lives in `global.anchors`.

---

## docs.json (navigation)

Navigation is tab-based: **tabs** → **groups** (label + icon) → **pages**
(referenced by path relative to `crux/docs/`, no `.mdx` extension). Nested groups
are supported (e.g. Paid Media under Dashboard Reports).

**Always add a new page to the right group in `docs.json`** or it will not appear
in the sidebar. When reorganising navigation, verify every page path corresponds
to an existing `.mdx` file before committing.

---

## Frontmatter requirements

Every page must include YAML frontmatter with exactly two fields:

```yaml
---
title: "Page Title Here"
description: "150-160 character SEO summary of what the page covers."
---
```

- **title:** 50–60 characters, descriptive and action-oriented for how-to guides.
- **description:** 150–160 characters, SEO-optimised.
- Do not add `sidebarTitle`, `icon`, or other frontmatter fields unless requested.

---

## Writing standards

- **British English** throughout (organisation, customisation, analyse, colour).
- **Never use em dashes**, use commas. **No emojis** in content.
- **Second person** ("you", "your"), operator-focused, problem-first narrative:
  lead with the reader's challenge, then present the solution. Active voice.
- Percentage changes are relative differences, not percentage points (master
  `<CRUX>/CLAUDE.md`).
- One H1 per page (the frontmatter title); H2/H3 only, sentence case, no skipped
  levels.
- Filenames `snake_case`, folders `kebab-case`, all lowercase.
- Internal links: root-relative, no `.mdx` (`/dashboard-suite/overview`);
  descriptive anchor text (never "click here"); verify the target exists.
- Language tags on every code block; alt text on every image. Media is
  supplementary, add it only when it aids comprehension.
- **Every page** ends with a horizontal rule and a CTA:
  `**Need help?** [Contact our team](mailto:support@gocrux.io) or [book a demo](https://gocrux.io/contact).`

### Components

Use the standard Mintlify components, following existing pages: `<CardGroup>` /
`<Card>` for navigation, `<AccordionGroup>` / `<Accordion>` for FAQs and
expandable detail, `<Steps>` / `<Step>` for sequential processes, callouts
(`<Info>`, `<Tip>`, `<Warning>`, `<Note>`), markdown tables for data
dictionaries, and Loom `<iframe>` embeds for report walkthroughs.

**Dashboard report pages** follow: Loom embed (if any) → overview paragraph →
data dictionary tables grouped by category → "Questions this report answers"
AccordionGroup → closing CTA. **Concept pages** follow: problem statement → how
it works → feature cards → CTA.

---

## Git workflow

Documentation changes go on `docs/{short-description}` branches and open a PR so
changes can be previewed before going live. Merging/pushing to `main` deploys to
production automatically.

1. `git checkout main && git pull origin main`, then
   `git checkout -b docs/{short-description}` (kebab-case:
   `docs/add-...`, `docs/update-...`, `docs/audit-...`, `docs/nav-...`).
2. Make changes, then stage **specific files by name** (never `git add -A`/`.`).
3. Commit with a `docs:` prefix, e.g. `docs: add budget optimiser report page`.
4. `git push -u origin docs/{short-description}` and open a PR with `gh pr create`.
5. Review the Mintlify PR preview; only merge once the user approves.
6. Commit frequently. NEVER use `--no-verify` or skip pre-commit hooks.

---

## Do not

- Skip frontmatter, or the title/description length rules, on any `.mdx` file.
- Use absolute URLs for internal links (root-relative, no `.mdx`).
- Include untested code examples or unverified product claims.
- Create new tabs/folders, or apply bulk audit fixes, without user approval.
- Add a page without adding it to the correct `docs.json` group.
- Commit directly to `main`, or use `git add -A` / `git add .`.
- Use em dashes, emojis, or American spellings.
