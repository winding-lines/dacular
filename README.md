# Dacular

## Install

```sh
curl -fsSL https://raw.githubusercontent.com/dacular-org/install/main/install.sh | sh
```

## Repository structure

```
site/       Astro site deployed to Cloudflare Workers (dacular.dev)
skills/     Claude skill definitions
  install-dacular/   Guided setup skill for the local AI stack
```

## Developing the site

```bash
cd site
npm install
npm run dev       # localhost:4321
npm run build     # production build to site/dist/
npm run deploy    # deploy to Cloudflare Workers
```

Pushes to `main` that touch `site/` are automatically deployed via GitHub Actions.
