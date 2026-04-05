# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository structure

```
site/       Astro site deployed to Cloudflare Workers
skills/     Claude skill definitions
  install-dacular/   Guided setup skill for the local AI stack
```

## Site commands

All commands run from `site/`:

```bash
cd site
npm run dev        # Start local dev server at localhost:4321
npm run build      # Build production site to site/dist/
npm run preview    # Preview build locally (astro build + wrangler dev)
npm run check      # Full verification: astro build + tsc + wrangler dry-run
npm run deploy     # Deploy to Cloudflare Workers
npm run cf-typegen # Regenerate Cloudflare Workers types
```

There are no test or lint scripts. Type checking runs as part of `astro build` and `tsc`.

Pushes to `main` that touch `site/` are auto-deployed via `.github/workflows/deploy.yml` using `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID` secrets.

## Site architecture

The Astro site lives entirely under `site/`. It is a static site (SSG) deployed to Cloudflare Workers via the `@astrojs/cloudflare` adapter.

### Content pipeline

Blog posts live in `site/src/content/blog/` as `.md` or `.mdx` files. The schema is defined in `site/src/content.config.ts` using Zod — fields are `title`, `description`, `pubDate`, `updatedDate` (optional), and `heroImage` (optional).

Dynamic routes in `site/src/pages/blog/[...slug].astro` call `getStaticPaths()` to pre-render every post at build time. The RSS feed (`rss.xml.js`) and sitemap (`@astrojs/sitemap`) are also generated at build time.

### Component model

- `site/src/components/BaseHead.astro` — injected into every page; handles canonical URLs, OG/Twitter meta, and font preloading
- `site/src/layouts/BlogPost.astro` — wraps individual post content
- `site/src/consts.ts` — `SITE_TITLE` and `SITE_DESCRIPTION` used across pages and the RSS feed

### Cloudflare integration

`site/astro.config.mjs` uses `@astrojs/cloudflare` with `platformProxy: { enabled: true }` so Cloudflare bindings are available locally. `site/wrangler.json` names the worker `dacular` and binds static assets from `./dist`.

## Skills

Skill definitions live in `skills/<skill-name>/`. Each skill is a markdown file with YAML frontmatter (`name`, `description`, `version`). The `install-dacular` skill is currently a placeholder.
