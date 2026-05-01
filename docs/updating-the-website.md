# Updating the Eclipse 30618 Website

This website is built with Astro and published automatically with GitHub Pages.

The live site is:

https://eclipse30618.com

## What You Need

Install these before editing the website:

- Git
- Node.js
- A code editor such as VS Code
- Access to the GitHub repository

## Project Structure

Important files and folders:

- `src/pages/index.astro`  
  The main homepage content.

- `src/styles/global.css`  
  The website styling.

- `public/`  
  Static files such as images, icons, and the custom domain file.

- `public/eclipse-hero.png`  
  The current homepage background image.

- `.github/workflows/deploy.yml`  
  The GitHub Actions deployment workflow. Do not edit this unless you are updating deployment settings.

- `public/CNAME`  
  The custom domain setting for GitHub Pages. Do not edit this unless the domain changes.

## Running the Website Locally

From the project folder, install dependencies:

```sh
npm ci
```

Start the local development server:

```sh
npm run dev
```

Astro will print a local URL, usually:

```txt
http://localhost:4321/
```

Open that URL in your browser to preview changes.

## Making a Simple Text Update

Most homepage text lives in:

```txt
src/pages/index.astro
```

Edit the visible text inside the HTML section.

After saving, check the browser preview. The local site should update automatically.

## Updating Styles

Website colors, spacing, fonts, and layout are in:

```txt
src/styles/global.css
```

Make small changes and preview them locally before committing.

Avoid changing large layout sections unless you have tested both desktop and mobile widths.

## Adding or Replacing Images

Put image files in:

```txt
public/
```

For example:

```txt
public/team-photo.jpg
```

Then reference the image from Astro or CSS using a root path:

```html
<img src="/team-photo.jpg" alt="Team photo" />
```

Use clear file names with lowercase letters and hyphens.

Good:

```txt
robot-2026.jpg
team-photo.jpg
sponsor-logo.png
```

Avoid:

```txt
IMG_1234.JPG
final final image.png
```

## Checking Your Work

Before pushing changes, run:

```sh
npm run build
```

This confirms the website can be built for production.

If the build fails, fix the error before pushing.

## Submitting Changes

Create a new branch:

```sh
git checkout -b update-homepage-text
```

Check changed files:

```sh
git status
```

Commit your work:

```sh
git add .
git commit -m "Update homepage text"
```

Push your branch:

```sh
git push origin update-homepage-text
```

Then open a pull request on GitHub.

## Publishing

When changes are merged into `main`, GitHub Actions automatically builds and deploys the site.

You can check deployment progress in the repository under:

```txt
Actions -> Deploy site to GitHub Pages
```

If the workflow succeeds, the site should update shortly after.

## Do Not Edit These Unless Asked

Avoid changing these files unless you are working with a mentor:

- `.github/workflows/deploy.yml`
- `public/CNAME`
- `package-lock.json`
- `astro.config.mjs`

These files control publishing, the domain, dependencies, and site configuration.

## Good Practices

- Preview locally before pushing.
- Keep commits focused on one change.
- Use descriptive commit messages.
- Check both desktop and mobile layouts.
- Do not commit very large image files unless needed.
- Ask for review before changing deployment or domain settings.

## Troubleshooting

If dependencies fail to install, try:

```sh
npm ci
```

If the local server is already running on a port, Astro may choose another port.

If the production site does not update immediately, check the GitHub Actions workflow first. If the workflow passed, wait a few minutes for GitHub Pages to refresh.
