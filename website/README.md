# Inferno — Website v2

Single-file, static HTML with an `/assets` folder. No build step required.
Drop everything at the root of any static host (Vercel, Netlify, Cloudflare
Pages, GitHub Pages, or plain S3 + CloudFront).

## What changed in v2

- Brand renamed to **Inferno** everywhere. Full legal name **Inferno Energies Pvt. Ltd.**
  appears only in the `<meta name="author">` tag and the footer copyright line.
- Logo (`logo.png`) integrated in nav and footer; favicon wired.
- Founder photo (`founder.webp` + `@2x` variant) in the Team section.
- Factory illustration (`factory.webp` + `@2x` variant) integrated into the Problem section.
- Beta-type Stirling animation (`stirling.gif`) replaces the CSS-drawn alpha schematic in the Technology section.
- **Model section fully restructured** around the three-pillar ecosystem:
  1. Energy Auditing
  2. WHR System Installation & Maintenance — with two side-by-side commercial models:
     - **Model A:** System Purchase + AMC (customer keeps electricity and carbon credits)
     - **Model B:** Energy-as-a-Service (zero CapEx, subsidised electricity subscription, Inferno monetizes credits, customer retains on-site Scope 1 & 2 emissions reduction)
  3. Energy Monitoring Dashboard — vendor-agnostic, compatible with non-Inferno WHR systems
- ROI table simplified (Simple-payback-scaled row removed).
- Contact email updated to `abhiram@inferno-energy.com` throughout (schema, CTA card, footer).
- LinkedIn link wired: `https://www.linkedin.com/company/inferno-energy/`
- "Primary"/"Secondary" tags removed from CTA cards.

## File inventory

```
/index.html                    76 KB — the entire site
/assets/logo.png               4.3 KB — nav/footer logo (64 px tall, transparent)
/assets/logo-large.png         23 KB — larger logo for marketing uses / OG image source
/assets/favicon.png            4.6 KB — browser tab icon (64 × 64)
/assets/founder.webp           14 KB — founder photo 1×
/assets/founder@2x.webp        22 KB — founder photo 2× (retina)
/assets/factory.webp           31 KB — problem-section illustration 1×
/assets/factory@2x.webp        42 KB — problem-section illustration 2× (retina)
/assets/stirling.gif           154 KB — beta-type Stirling engine animation
```

**Total first-paint payload on desktop:**
~`index.html` (15 KB gzipped) + `logo.png` (4 KB) + `favicon.png` (5 KB) + fonts.

**Lazy-loaded below the fold:** `factory.webp`, `stirling.gif`, `founder.webp`.

## Performance profile

- Uncompressed HTML: ~76 KB
- Over the wire (gzipped HTML): ~15 KB
- External requests: 1 (Google Fonts CSS) + font files
- JS: ~40 lines of vanilla, no libraries
- All below-fold images have `loading="lazy"`
- Retina-aware `srcset` on founder and factory images
- All CSS animations respect `prefers-reduced-motion`

## Remaining placeholders / TODO before launch

Search `index.html` for these hrefs:

| Href | What's needed |
|---|---|
| `#assessment` (first CTA card) | Point to a Typeform/Tally/custom survey URL for the pilot program |
| `#whitepaper` (third CTA card, footer link) | Upload technical whitepaper PDF and link to it |
| `#privacy`, `#terms` (footer) | Add privacy policy and terms of service pages |
| `og:image` meta tag | Create a 1200×630 social-share image and host at `/og-image.jpg` |

## Deploying to www.inferno-energy.com

1. Host on Vercel (free tier) or equivalent.
2. Upload `index.html` and the `/assets` folder, preserving paths.
3. Point DNS for `inferno-energy.com` and `www.inferno-energy.com` at the host.
4. Configure a 301 redirect between the two hosts (pick one canonical — typically `www.`).
5. Enable automatic HTTPS (Vercel/Netlify/Cloudflare all do this by default).
6. Add analytics: Plausible or PostHog is enough; one `<script>` before `</head>`.

## Design tokens (for future consistency)

Colors, spacing, and type scale are defined as CSS variables in `:root`.
Copy that block into any future page or stylesheet to stay on-brand.

```css
--bg: #F4EFE7;          /* warm off-white base */
--bg-alt: #EDE6DA;      /* alternating sections */
--bg-deep: #1C1917;     /* inverted sections (Ecosystem, Footer) */
--ink: #1C1917;         /* body text */
--ink-muted: #5A534C;   /* secondary text */
--ember: #D9422D;       /* primary accent (matches logo red) */
--coolant: #1E3A5F;     /* cold-side technical accent */
```

Fonts: Instrument Serif (display) + IBM Plex Sans (body) + IBM Plex Mono (data).
