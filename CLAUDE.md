# Website rules for Claude

This repository is one company's public website, hosted on Cloudflare Pages and edited through SEED (CSOS's website builder) or from a chat. Read this before every change.

The repository itself is public, and so are its commit history and workflow logs. Never put passwords, API keys, tokens or private notes in any file or commit message. Keys belong in GitHub, Cloudflare or Zite settings, never in the code.

## What's where

- `site/` is the website. Every file in it is public, and Cloudflare serves it exactly as it is: there's no build step.
- `site/assets/css/site.css` is the only stylesheet. The brand's colors, fonts and spacing are variables at the top. Change those rather than hard-coding values in pages.
- `site/assets/js/site.js` is the only script (the mobile menu). Keep JavaScript to small, optional touches.
- `site/_redirects` lists old URLs that must keep working, in Cloudflare Pages format.
- `site/_headers` sets security headers. Its `frame-ancestors` rule lets SEED show the site in a frame. Keep it, and never add `X-Frame-Options`.
- `site/sitemap.xml` lists every page that search engines should index.
- `.github/` holds the workflows that run you. Never touch it.

## How to edit

- Plain HTML, CSS and a little vanilla JavaScript. No frameworks, build tools, npm packages or new third-party scripts unless the request explicitly asks for one.
- Mobile-first and fast. Check that every layout works at 360px wide. Keep images under 300 KB, and give every image `width`, `height` and meaningful `alt` text (empty `alt=""` only for decoration).
- Every page has one H1, a unique `<title>` under 60 characters, a meta description under 160 characters, and a canonical link to its live URL.
- The header and footer are repeated in every page. When you change one, change it the same way on every page.
- Keep every existing URL working. If a page is removed or renamed, add a 301 line to `site/_redirects` and update `site/sitemap.xml`.
- Embeds (forms, scheduling, maps) are iframes or script tags supplied by those services. Copy their codes exactly and don't rebuild them.
- New photos go in `site/assets/img/`. Resize large photos to at most 1600px wide before using them.
- Keep the meaning of the company's text. Fix typos only when asked, and never invent facts such as prices, licenses, awards or reviews.
- Accessibility: real links and buttons, visible focus outlines, text contrast of at least 4.5:1, and form fields with labels.

## Branches

- `main` is the live site. It changes only when Steven approves in SEED, which merges `preview` into `main`.
- `preview` is where every change goes first. It's served at preview.<domain>, which search engines are told to skip.
- In a GitHub Actions run, don't commit, push or create branches: the workflow commits your changes to `preview` after you finish.
- In a chat session, commit only to `preview` and push `preview`. Never push to `main`.

## When you finish

End with a short plain-English summary for the site owner: what changed and on which pages, anything you couldn't do, and anything they should check. Skip code and file paths unless they help.
