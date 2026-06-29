# CLAUDE.md — Amie's Design System

Context for Claude Code. Read this before making changes.

## What this repo is

The central design system (single source of truth) for Amie's projects.
It holds design tokens and a storybook preview page. Consumer projects
(portfolio, future products) vendor a copy of the CSS. This repo contains
only the system and its preview, never the consumer apps.

## Files

- `amies-design-system.css` — all design tokens (CSS custom properties). This
  is the single source of truth. Edit tokens here only.
- `amies-design-system.html` — storybook / preview page that documents every
  token and component. Links the CSS above.
- `README.md` — usage, local preview, layering principle.

Live preview: https://amysalami.github.io/amies_design_system/amies-design-system.html

## Token system (the rules that matter)

Two-color brand system:
- `--accent` (#ffc400, amber) is PRIMARY. Use for fills and icons ONLY,
  never for text.
- `--secondary` (#1e3258, navy) is SECONDARY. Use for headings, labels, and
  any text sitting on a primary fill.
- Text on a primary (amber) surface must be `--secondary`, not white.

Other tokens: `--paper`, `--paper-2`, `--ink`, `--ink-soft`, `--line`,
`--accent-soft`, `--sage`, `--highlight`, layout (`--max`, `--wide`,
`--gutter`), radius (`--r-xs/sm/md/lg/pill`), elevation
(`--shadow-pill/lift/panel`). Fonts: Fraunces (display), Hanken Grotesk (body).

## Layering principle

- Foundations (tokens): live here, shared by all projects.
- Shared components (buttons, badge, card): may live here once genuinely reused.
- Project-specific components (e.g. a portfolio roadmap, a product data table):
  stay in that project, do not push them into this central repo.

## Local preview

Serve over http (not file://) so the CSS loads:

```bash
python3 -m http.server 8000
# open http://localhost:8000/amies-design-system.html
```

## Storybook preview conventions

When adding a new component to `amies-design-system.html`, follow this rule for
whether to wrap it in `.ds-stage`:

- **Use `.ds-stage`** when the component has no visible frame of its own.
  Examples: buttons, badges, tags, nav bar, pull quote.
- **Omit `.ds-stage`** when the component already has its own border or
  container. The component's own chrome is the demo.
  Examples: paper-card, glance (label grid), imgslot.

## Editorial conventions (kept across all surfaces)

- No em dashes or en dashes anywhere. Use commas or periods.
- Colons only as bold semi-heading lead-ins, never mid-sentence.
- Claims are evidence-based, not feeling-based.

## Distribution

Consumers currently use Path B (a vendored copy of `amies-design-system.css`).
When a second product appears, move to an npm package so updates sync via
`npm update` instead of manual copying.
