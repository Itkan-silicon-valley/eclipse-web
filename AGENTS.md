# Agent Guide for eclipse-web

This repo contains the public website for FTC Team Eclipse 30618.

Production site:

- `https://eclipse30618.com`

## Tech Stack

- Astro static site
- Plain Astro pages and CSS
- GitHub Pages deployment through GitHub Actions
- npm for dependencies

## Important Commands

Install dependencies:

```sh
npm ci
```

Run locally:

```sh
npm run dev
```

Build production output:

```sh
npm run build
```

Preview production build:

```sh
npm run preview
```

Always run `npm run build` before committing website changes.

## Repository Layout

- `src/pages/index.astro`  
  Homepage placeholder page.

- `src/pages/counter.astro`  
  Unlinked elapsed-time counter page at `/counter/`. This page will be removed later on.

- `src/styles/global.css`  
  Shared styling for the homepage and counter page.

- `public/`  
  Static assets copied directly into the built site.

- `public/eclipse-hero.png`  
  Main background image used by both pages.

- `public/favicon.svg`  
  Site favicon.

- `public/CNAME`  
  GitHub Pages custom domain. Do not change unless the domain changes.

- `.github/workflows/deploy.yml`  
  GitHub Pages deployment workflow. Be careful when editing.

- `docs/updating-the-website.md`  
  Student-facing instructions for updating the site.

## Pages

Homepage:

- Source: `src/pages/index.astro`
- Route: `/`
- Purpose: simple public placeholder for Eclipse 30618.

Counter page:

- Source: `src/pages/counter.astro`
- Route: `/counter/`
- Purpose: live elapsed-time counter. This page will be removed later.
- Start timestamp: `2026-04-29T21:45:00-07:00`
- Display label: `April 29, 2026 at 9:45 PM PDT`
- This page is intentionally not linked from the homepage.

## Styling Guidelines

- Keep the visual style consistent with the existing dark eclipse/robotics theme.
- Shared CSS lives in `src/styles/global.css`.
- Use responsive layout rules for mobile and desktop.
- Do not add large new frameworks or UI libraries for simple pages.
- Avoid changing homepage behavior when adding unlinked utility pages.

## Deployment

Deployments happen automatically when changes are pushed to `main`.

The workflow:

- installs dependencies with `npm ci`
- builds with `npm run build`
- uploads `dist/`
- deploys to GitHub Pages

The workflow currently uses Node 24-ready GitHub Actions and sets:

```yaml
FORCE_JAVASCRIPT_ACTIONS_TO_NODE24: true
```

Do not downgrade the action versions or remove that setting without a reason.

## Domain Notes

The custom domain is configured in:

```txt
public/CNAME
```

Current value:

```txt
eclipse30618.com
```

Do not edit `public/CNAME` unless the domain is changing.

## Dependency Notes

The repo includes `.npmrc` to force the public npm registry:

```txt
registry=https://registry.npmjs.org/
```

Keep this file. It prevents CI from using a local/private npm registry when `package-lock.json` is regenerated.

## Safe Change Checklist

Before finishing a change:

1. Run `npm run build`.
2. Confirm the changed route builds.
3. Check `git status --short`.
4. Do not commit generated `dist/` or `node_modules/`.
5. Do not modify deployment or domain files unless the task requires it.

## Files Usually Safe to Edit

- `src/pages/*.astro`
- `src/styles/global.css`
- `public/` assets, when adding or replacing website images
- `docs/*.md`
- `README.md`

## Files to Treat Carefully

- `.github/workflows/deploy.yml`
- `public/CNAME`
- `astro.config.mjs`
- `package.json`
- `package-lock.json`
- `.npmrc`

## Git Guidance

- Keep commits focused.
- Do not push unless explicitly asked.
