# crux/docs/ — Technical Context

The Crux help centre at docs.gocrux.io. Inherits master context from
`<CRUX>/CLAUDE.md` and platform context from `<CRUX>/crux/CLAUDE.md`.

GitHub repo: `go-crux/docs`. Content is for founders, heads of growth and CFOs,
not engineers.

For anything beyond a quick edit (new pages, navigation changes, audits), use the
**`help-centre`** agent (`.claude/agents/help-centre.md`), which holds the full
writing conventions, component patterns and branch/PR workflow.

---

## Tech stack

- **Mintlify** — docs framework. Config in `docs.json` (theme `mint`, navigation,
  navbar, footer). All content is `.mdx`.
- **GitHub** (`go-crux/docs`) — pushes to `main` trigger automatic deployment via
  the Mintlify GitHub app. No build step to run locally beyond `mint dev`.
- Local preview: `npm i -g mint` then `mint dev` from the repo root (where
  `docs.json` lives) → `http://localhost:3000`.

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

Navigation is tab-based: **tabs** → **groups** (label + icon) → **pages**
(referenced by path, no `.mdx` extension). Nested groups are supported (e.g. Paid
Media under Dashboard Reports). Persistent links live in `global.anchors`.
**Always add a new page to the right group in `docs.json`** or it won't appear in
the sidebar.

---

## Conventions

- **British English** throughout (organisation, customisation, analyse, colour).
- **Never use em dashes**, use commas. **No emojis** in content.
- **Second person** ("you", "your"); operator-focused, problem-first narrative.
- Frontmatter on every page: `title` (50–60 chars) and `description` (150–160
  chars for SEO). No other frontmatter fields unless requested.
- One H1 per page (the frontmatter title); H2/H3 only, sentence case, no skipped
  levels.
- Filenames `snake_case`, folders `kebab-case`, all lowercase.
- Internal links: root-relative, no `.mdx` (`/dashboard-suite/overview`);
  descriptive anchor text, verify the target exists.
- Percentage changes are relative differences, not percentage points (master
  `<CRUX>/CLAUDE.md`).

---

## Deployment

Merging/pushing to `main` deploys to production automatically. The `help-centre`
agent works on `docs/{short-description}` branches and opens a PR (Mintlify builds
a preview deployment per PR) so changes can be reviewed before going live.
