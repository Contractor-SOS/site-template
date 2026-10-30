# Site template

This repo, like every site repo, is public: never commit passwords, API keys or tokens.

The starting point for every company website CSOS hosts: plain HTML and CSS on Cloudflare Pages, edited through SEED or from a chat with Claude.

## Make a new site from this template

1. Capture the old site first, in its own folder in the private `site-archive` repo.
2. On this repo's page, click **Use this template → Create a new repository**. Owner `Contractor-SOS`, name `<company>-website`, **Public**. The organization's `CLAUDE_CODE_OAUTH_TOKEN` secret covers public repos, so there's no secret to add.
3. In the new repo, create a `preview` branch from `main`.
4. Fill in `site/` with the company's pages, contact details, brand colors and fonts (the variables at the top of `site/assets/css/site.css`), or ask Claude to do it from the old site's capture.
5. Cloudflare → **Workers & Pages → Create → Pages → Connect to Git** → pick the repo. Production branch `main`, build command left empty, build output directory `site`, preview deployments for the `preview` branch only.
6. Add the site to SEED's Sites table.

The full process, including moving a domain to Cloudflare and going live, is in the Websites runbook in the App Ecosystem HQ project.

## What's in here

| Path | What it is |
| --- | --- |
| `site/` | The website. Cloudflare Pages publishes exactly this folder |
| `site/assets/css/site.css` | The only stylesheet; brand variables at the top |
| `site/_redirects`, `site/_headers` | Old-URL redirects and security headers (Cloudflare Pages format) |
| `CLAUDE.md` | The rules Claude follows when editing |
| `.github/workflows/` | The caller for the shared Claude edit workflow in `site-tools` |

## Branches

`main` is the live site. `preview` is where every change goes first, served at preview.<domain>. Going live is merging `preview` into `main`, which SEED does when Steven presses Approve.
