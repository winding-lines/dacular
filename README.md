# Dacular

Dacular is an experimental project that lets you run a local AI agent stack on a Mac mini and expose it as a Claude skill others can install.

## What it is

The stack has two components running locally:

- **[zeroclaw](https://github.com/zeroclaw)** — agent framework
- **[Modular Max](https://www.modular.com/max)** — inference engine running Gemma3

Users install the `install-dacular` skill from the Claude skill marketplace and follow the guided setup to get both systems running and talking to each other on their own Mac mini.

## How the setup works

The skill walks through these steps:

1. **Create a dedicated macOS account** — a clean user account with none of your personal data, used exclusively for the AI stack.
2. **Install zeroclaw** — agent framework installed into the new account.
3. **Install Modular Max with Gemma3** — local inference engine, configured to accept requests from zeroclaw.
4. **Wire them together** — configure zeroclaw to use the local Max endpoint for inference.
5. **Data isolation** — personal data lives in your main account. You can mount it from there to work with it, but the mount must be removed before starting Claude — private data is never accessible while Claude is running.

## Platform support

Currently **Mac mini only**.

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
