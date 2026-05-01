# Eclipse 30618 Public Website

Static Astro site for `eclipse30618.com`.

## Development

```sh
npm install
npm run dev
```

## Build

```sh
npm run build
npm run preview
```

## Publishing

The site deploys to GitHub Pages from `.github/workflows/deploy.yml` when
changes are pushed to `main`.

The custom domain is configured through `public/CNAME`.
