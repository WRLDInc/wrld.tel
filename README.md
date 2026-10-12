# wrld.tel

**WRLD.Tel** — business VoIP phone systems with AI call analysis, from WRLD Tech Co. (a DBA of WRLD Inc.). Cloud telephony on Telzio's enterprise platform, AI transcription and sentiment, call intelligence, and a real-time dashboard at [dash.wrld.tel](https://dash.wrld.tel).

Live at [https://wrld.tel](https://wrld.tel).

## Stack

- Static HTML and CSS. No build step, no framework, no third-party JS.
- Design: the [WRLD design system](https://wrld.design) ([WRLDInc/DesignSystem](https://github.com/WRLDInc/DesignSystem)). Tokens, type and the self-hosted typefaces (Montserrat, Ubuntu, Ubuntu Mono) are linked from `https://wrld.design/styles.css`; a fallback copy of the tokens is inlined so the page renders correctly if that origin is unreachable. Light, dark and auto themes via `data-theme`, sharing the `wrld-theme` localStorage key with other WRLD properties.
- Icons: inline [Lucide](https://lucide.dev) SVGs at 1.5px stroke. The starburst mark is inline SVG; favicons are the wrld.design set under `logos/favicons/`.
- Hosting: [Cloudflare Pages](https://pages.cloudflare.com).

## Deploy

```bash
npx wrangler pages deploy . --project-name=wrld-tel-website
```

Or connect this repo to Cloudflare Pages for automatic deploys on push.

| Setting | Value |
|---------|-------|
| Build command | *(none — static site)* |
| Build output directory | `/` |
| Custom domain | `wrld.tel` |

`_headers`, `_redirects`, `robots.txt`, `sitemap.xml` and `llms.txt` live at the repo root so Pages serves them from the site root.

## Local preview

```bash
python3 -m http.server 8788
```

## Structure

```
.
├── index.html            # Landing page: hero, features, how it works, industries, pricing, FAQ, WRLD family
├── privacy.html          # Privacy policy (served at /privacy)
├── terms.html            # Terms of service (served at /terms)
├── og-template.html      # Source for og-image.png (see below)
├── og-image.png          # 1200×630 social card
├── llms.txt              # Agent-readable overview (llmstxt.org)
├── robots.txt            # Crawler directives + Content Signals
├── sitemap.xml
├── _headers              # Cloudflare security + cache headers
├── _redirects            # Clean URLs and convenience paths (/login, /support, /status…)
├── logos/                # Starburst mark (PNG) and favicon set from wrld.design
└── wrangler.toml
```

## SEO and discoverability

- Expanded, sentence-case copy covering business VoIP, AI call analysis, call intelligence, onboarding, industries, pricing philosophy and an eight-question FAQ.
- JSON-LD graph: `Organization` (WRLD Tech Co. / WRLD Inc.), `WebSite`, `Service` with an offer catalog, and `FAQPage`.
- Open Graph and Twitter cards with a 1200×630 image; canonical URLs; `robots.txt` with Content Signals (`search=yes, ai-input=yes, ai-train=no`); `sitemap.xml` with image extension; `llms.txt`.
- Crosslinks to the WRLD family: wrld.tech, WRLD.Services, WRLD.host, WRLD.AI, WRLD.Support, WRLD.help, wrld.design, WRLD.Press, WRLD.One, portal.wrld.tech, status.wrld.host, roadmap.wrld.tech, calendar.wrld.tech, and Telzio.

## Regenerating the social image

```bash
"/Applications/Google Chrome Beta.app/Contents/MacOS/Google Chrome Beta" --headless=new --disable-gpu \
  --hide-scrollbars --virtual-time-budget=8000 --screenshot="$PWD/og-image.png" --window-size=1200,630 \
  "file://$PWD/og-template.html"
```

## Analytics

No tag manager is included. Add one deliberately (and update `_headers` if a CSP is introduced).

## Related

- [dash.wrld.tel](https://dash.wrld.tel) — WRLD.Tel portal ([WRLDInc/telzioWRLD](https://github.com/WRLDInc/telzioWRLD))
- [wrld.design](https://wrld.design) — design system
- [wrld.one](https://wrld.one) — directory of WRLD services
