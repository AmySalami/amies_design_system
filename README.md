# Amie's Design System

[![Open Live Preview](https://img.shields.io/badge/Open-Live_Preview-ffc400?style=for-the-badge&labelColor=1e3258)](https://amysalami.github.io/amies_design_system/amies-design-system.html)

Open the live preview: https://amysalami.github.io/amies_design_system/amies-design-system.html

The central design system (design tokens and reusable components) for every project.
This is the single source of truth, edit a token here and only here.

## Structure

```
.
├── amies-design-system.css     # tokens (color, font, spacing, radius, elevation)
├── amies-design-system.html    # the preview page for the system
└── README.md
```

This repo holds only "the system itself" and "the preview page". The projects that
actually use it (portfolio, products) are consumers in their own repos, not in here.

## Local preview

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000/amies-design-system.html`
(it has to be served over http, not by double clicking the file open directly)

## Editing tokens

Edit a value in `amies-design-system.css` (for example `--accent`), then commit and push.
The preview page updates immediately. Each consumer has to be synced separately
(see the process in that repo's README).

Bump `Version` in the header comment of `amies-design-system.css` and tag the commit
(`git tag v1.0.1 && git push --tags`). A consumer vendors the file by copying it, so
the number in the header is the only way to tell which copy it has.

## Layering

What belongs in this repo vs what stays with the project itself:

- **Foundations (here):** all tokens, shared by every project.
- **Shared components (can live here):** buttons, badge, card, the things genuinely
  reused across several projects.
- **Project specific components (stay with the project):** for example the roadmap
  nodes of the portfolio, the data table or form of a product. Do not push those
  into the central system.

> The principle: promote something into the shared layer only once it is genuinely
> reused. Do not promote something that is used in one place.

## Colour usage

- **Primary `--accent` (#ffc400)** is for surfaces and icons only, never for text.
- **Secondary `--secondary` (#1e3258)** is for headings, labels, and text sitting on a
  primary surface.

## Hosting online

Push to GitHub and turn on GitHub Pages, or connect Netlify / Vercel, so the preview
page has a web link the team can open.
