# Miss Floss — The AI Dental Receptionist

Landing site for **Miss Floss**, the AI dental receptionist that answers every patient call, books every appointment, and verifies insurance — 24/7, in 40+ languages.

## Stack
Single-page static HTML site (rebrand of a Webflow Ecommerce template). All visual assets, CSS, and Lottie animations are hosted on the original Webflow CDN; only the copy and CTAs have been rewritten for Miss Floss.

## Run locally
```bash
python3 -m http.server 8080
```
Then open http://localhost:8080.

## CTA
Every "Book a Demo" / "Book Now" button routes to:
`https://cal.com/missfloss/demo?overlayCalendar=true`

## Deploy
Drop `index.html` on any static host — Netlify, Vercel, Cloudflare Pages, or GitHub Pages. No build step.
