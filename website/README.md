# Inferno Website — Deployment Ready

Everything needed to go live at **www.inferno-energy.com**.

## What's in this folder

```
├── index.html                 The homepage
├── privacy.html               Privacy Policy (DPDP-aligned)
├── terms.html                 Terms of Use
├── robots.txt                 Search-engine crawl rules
├── sitemap.xml                List of pages for Google
├── vercel.json                Deployment config (optional, Vercel only)
└── assets/
    ├── logo.png               Logo for nav / footer
    ├── logo-large.png         Larger logo (kept for future use)
    ├── favicon.png            Browser tab icon
    ├── og-image.jpg           1200×630 social share preview
    ├── factory.webp + @2x     Landing section illustration
    ├── smoke.webp + @2x       Problem section illustration
    ├── founder.webp + @2x     Team section photo
    └── stirling.gif           Technology section animation
```

## Total payload
- HTML pages: ~100 KB uncompressed, ~20 KB gzipped
- Critical images (above-fold): logo + favicon only = ~10 KB
- Everything below the fold is lazy-loaded

## Changes made in this round

1. **Technical Overview CTA hidden** — the third card is commented out in the HTML (not deleted). The CTA grid rebalances to 2 cards on a centered 960-px max-width. The "Overview" link is also removed from the footer.
   - **To restore later:** open `index.html`, search for `ctaOverview`, uncomment the `<a>` block, and remove the `cta-grid-2` class from the parent `<div>`. Replace `./assets/technical-overview.pdf` with your actual PDF URL.

2. **Privacy Policy** — `privacy.html` is a DPDP-Act-aligned policy. It covers: identity, data collected, purposes, sharing, cookies, user rights, retention, grievance officer. Edit the contact details if needed.

3. **Terms of Use** — `terms.html` covers: site use, IP, no-warranty disclaimer, limitation of liability, governing law (Hyderabad jurisdiction).

4. **OG Image** — `assets/og-image.jpg` (63 KB). Matches the site's actual fonts and palette. Used automatically when the URL is shared on LinkedIn, WhatsApp, Twitter, Slack, etc.

5. **robots.txt + sitemap.xml** — tells Google what to index.

6. **vercel.json** — sets cache headers and basic security headers if you deploy to Vercel.

---

## Deployment — the shortest path

### Option A: Vercel (recommended)

1. Go to **[vercel.com](https://vercel.com)** and sign up (free).
2. On the dashboard, click **"Add New... → Project"** then **"Deploy a Static Site"**.
3. You can either connect a GitHub repo or drag-and-drop this whole folder into the web UI.
4. Vercel gives you a temporary URL (e.g. `inferno-xxxxx.vercel.app`). Open it and verify the site looks right.
5. **Settings → Domains** → add `inferno-energy.com` and `www.inferno-energy.com`.
6. Vercel shows you DNS records. Copy them into your domain registrar's DNS settings (wherever you bought the domain).
7. Wait up to an hour for DNS to propagate. HTTPS is automatic.

### Option B: Netlify

1. Sign up at **[netlify.com](https://netlify.com)** and drag this folder onto the dashboard.
2. You get a temporary URL. Verify the site.
3. **Site settings → Domain management** → add `www.inferno-energy.com` and follow their DNS instructions.

### Option C: Cloudflare Pages

1. Sign up at **[pages.cloudflare.com](https://pages.cloudflare.com)**.
2. If your domain is already on Cloudflare, deployment is a single zip upload.
3. Custom domain config is one click.

All three are free at this scale. Vercel is the most common and has the least friction for this setup.

---

## Before you go live, double-check

- [ ] Open `index.html` locally and click every nav link, every CTA, every footer link. Confirm scrolling and mobile layout.
- [ ] **Pilot program button** currently points to `#assessment` (non-functional). Create a Tally/Typeform survey, then replace `#assessment` in `index.html` with the real URL.
- [ ] Confirm `abhiram@inferno-energy.com` is set up to receive email. Test by sending a message to yourself.
- [ ] Confirm the LinkedIn page at `https://www.linkedin.com/company/inferno-energy/` is live and published.

## Post-launch, first week

1. **Add analytics** — sign up at [plausible.io](https://plausible.io) (30-day free trial) or use Google Analytics 4 if you prefer. Either way, you'll get a single `<script>` tag to paste into `index.html` just before `</head>`.
2. **Submit to Google Search Console** — go to [search.google.com/search-console](https://search.google.com/search-console), verify ownership, submit the sitemap (`https://www.inferno-energy.com/sitemap.xml`).
3. **Test the social preview** — paste `https://www.inferno-energy.com` into [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) and [Twitter Card Validator](https://cards-dev.twitter.com/validator) to confirm the OG image loads.
4. **Announce on LinkedIn** — personal post linking the site, tagged with relevant cleantech and BITS/RWTH communities.

## Future additions (no urgency)

- Technical Overview PDF → uncomment the third CTA, drop the PDF at `/assets/technical-overview.pdf`.
- Case studies once you have pilots — add as a new section between Industries and Team.
- Blog / press page — add as a new sub-page and link from the nav and footer.
- Update `<meta name="author">` and the JSON-LD schema's `foundingDate` if the incorporation date of the Pvt. Ltd. differs from 2025.

---

## Design tokens (reference)

All colors and spacing live in the `:root` block at the top of each HTML file's `<style>` section. If you ever add more pages, copy that block and the font-family declarations to stay consistent.

```css
--bg: #F4EFE7;          /* warm off-white base */
--bg-alt: #EDE6DA;      /* alternating sections */
--bg-deep: #1C1917;     /* inverted sections */
--ink: #1C1917;         /* body text */
--ink-muted: #5A534C;   /* secondary text */
--ember: #D9422D;       /* primary accent */
--coolant: #1E3A5F;     /* cold-side accent */
```

Fonts: Instrument Serif (display) + IBM Plex Sans (body) + IBM Plex Mono (data/eyebrows).
