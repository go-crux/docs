# Analysis Framework, drop-in instructions

This bundle adds a four-page Analysis Framework section to your Mintlify docs. It contains a hub page plus three pillar sub-pages, with five SVG diagrams.

## File structure

Drop the `analysis-framework/` folder into the root of your `go-crux/docs` repo, alongside `dashboard-suite/`, `health-metrics/` etc.

```
go-crux/docs/
├── analysis-framework/
│   ├── overview.mdx
│   ├── customers.mdx
│   ├── frequency.mdx
│   ├── aov.mdx
│   └── images/
│       ├── growth-equation.svg
│       ├── decision-flowchart.svg
│       ├── metric-tree-customers.svg
│       ├── metric-tree-frequency.svg
│       └── metric-tree-aov.svg
└── docs.json
```

## docs.json update

Add this tab to the `tabs` array in `docs.json`. Suggested position: between **Overview** and **Dashboard Suite**, since it's a conceptual layer that supports both.

```json
{
  "tab": "Analysis Framework",
  "groups": [
    {
      "group": "Getting Started",
      "icon": "compass",
      "pages": [
        "analysis-framework/overview"
      ]
    },
    {
      "group": "The Three Pillars",
      "icon": "layer-group",
      "pages": [
        "analysis-framework/customers",
        "analysis-framework/frequency",
        "analysis-framework/aov"
      ]
    }
  ]
},
```

## Notes

- All five SVGs use Crux brand colours (`#0A1929` background, `#57AAF6` primary, `#C87DBB` and `#5E9766` for pillar accents). Yellow `#FBBC09` is not used as it's reserved for the logo per the brand guidelines.
- Images are referenced in the MDX using absolute paths (`/analysis-framework/images/...`), which is the convention Mintlify expects for static assets in subfolders.
- The MDX uses standard Mintlify components (`Frame`, `Card`, `CardGroup`, `Steps`, `Step`, `Tabs`, `Tab`, `Accordion`, `AccordionGroup`, `Note`). No additional dependencies needed.
- Cross-links to existing pages (e.g. `/dashboard-suite/channel_performance`) assume your current URL structure. Adjust if the routes change.

## After publishing

The Loom walkthrough you mentioned can be embedded into the hub page using Mintlify's `<iframe>` support, or by adding a video URL. Easiest spot is just below the "The growth equation" section, so people can watch the walkthrough before reading the rest.
