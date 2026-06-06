# MissFloss.ai — Landing Site

Single-page marketing site for MissFloss.ai, positioned as an AI platform for dental practices (patient communication, recall, treatment plan follow-ups). Rebranded from the VoiceCloud Webflow template, served as static HTML.

## Folder structure

```
miss-floss/
  index.html      # Full landing page. Single file, no build step.
  logo.svg        # Brand mark (currently unused in markup — nav and footer use the "MissFloss.ai" wordmark text)
  README.md
  CLAUDE.md       # This file
  .gitignore
```

No build tooling. No package.json. Open `index.html` in a browser and it renders.

## How the page is wired

- **Base template:** VoiceCloud / BRIX Webflow export. The shared CSS, runtime JS, and image assets are still pulled from `cdn.prod.website-files.com` over HTTPS. Do NOT strip the `data-wf-domain` / `data-wf-page` / `data-wf-site` attributes on `<html>` — Webflow's IX2 interaction engine uses them to find and play the scroll-in animations. Every section starts at `opacity: 0; filter: blur(8px)` inline; without IX2 init, the entire page renders invisible.
- **Webflow badge:** auto-injected by `webflow.0b4eec26....js`. Hidden via the `<style>` block in `<head>` (`.w-webflow-badge { display: none !important }`). Keep that rule — do not try to remove the badge by stripping the `data-wf-*` attributes (that breaks animations, see above).
- **Brand wordmarks:** nav and footer use plain text styled via `.brand-wordmark` / `.footer-brand-wordmark` in the inline `<style>` block. The original SVG logo references were removed.
- **CTA:** every "Book a demo" button points to `https://cal.com/missfloss/demo?overlayCalendar=true` and opens in a new tab.

## Page sections (in order)

1. Hero — "AI that grows your dental practice"
2. Logo strip — "Trusted by forward-thinking practices"
3. About — "Built for the way modern dental teams actually work"
4. Features grid — patient communication, treatment plan follow-ups, recall, PMS integrations, HIPAA security
5. How it works — Connect PMS → Train voice → Go live (tabbed)
6. CTA section
7. Testimonials slider — 4 practice-owner quotes with metrics
8. FAQ — PMS support, HIPAA, onboarding, front-desk impact, pricing
9. Footer

## Editing rules

- **Copy changes:** edit `index.html` directly. No templates, no partials.
- **Never add em dashes** to any copy. Use commas, periods, or rewrite.
- **Keep CTAs pointing to** `https://cal.com/missfloss/demo?overlayCalendar=true`. If the demo link ever changes, find/replace all occurrences in `index.html` (there are ~9 instances).
- **Image assets** are still on Webflow's CDN. When MissFloss.ai brand assets are ready, replace the CDN URLs with paths to a local `/assets/` folder and commit those images alongside.
- **Logo upgrade:** when you want to swap the text wordmark for `logo.svg` (or a new asset), replace the `<a class="header-logo ...">MissFloss.ai</a>` and the matching footer link with `<img>` tags. Remove the `.brand-wordmark` / `.footer-brand-wordmark` style block if no longer used.

## Deployment

Not yet wired to a host. Options:
- **Netlify drop:** drag `index.html` onto netlify.com. Single file deploys.
- **Vercel:** `vercel --prod` from this directory. No framework, treated as static.
- **GitHub Pages:** enable Pages on the `main` branch root in the repo settings.

If deploying via Vercel CLI, remember: `git add` + `git commit` before `vercel deploy --prod --yes`. Vercel deploys from git HEAD, not the local filesystem.

## Repo

- Remote: `https://github.com/toprmrproducer/miss-floss-site`
- Branch: `main`
