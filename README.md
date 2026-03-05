# wrld.tel

Marketing landing page for **WRLD VoIP Systems** — AI-powered call analysis built on Telzio's enterprise VoIP platform.

**Live:** [https://wrld.tel](https://wrld.tel)

## Stack

- Static HTML + [Tailwind CSS](https://tailwindcss.com) (CDN)
- Hosted on [Cloudflare Pages](https://pages.cloudflare.com)
- Google Tag Manager for analytics

## Deploy

```bash
npx wrangler pages deploy . --project-name=wrld-tel-website
```

Or connect this repo to Cloudflare Pages for automatic deploys on push.

### Cloudflare Pages Settings

| Setting | Value |
|---------|-------|
| Build command | *(none — static site)* |
| Build output directory | `/` |
| Custom domain | `wrld.tel` |

## Structure

```
.
├── index.html            # Main landing page
├── privacy.html          # Privacy policy
├── terms.html            # Terms of service
├── wrangler.toml         # Cloudflare Pages config
└── public/
    ├── robots.txt        # Crawler directives
    ├── sitemap.xml       # Sitemap for search engines
    ├── _headers          # Cloudflare security headers
    └── _redirects        # Clean URL routing
```

## GTM Setup

Replace `GTM-XXXXXXX` in `index.html` with your actual Google Tag Manager container ID.

## SEO

- Open Graph + Twitter Card meta tags
- JSON-LD structured data (Organization + WebSite)
- Canonical URLs
- `robots.txt` + `sitemap.xml`
- Semantic HTML with ARIA landmarks
- Security headers via `_headers`

## Related

- [callanalysis.wrld.tel](https://callanalysis.wrld.tel) — Call analysis dashboard
- [api.voip.wrld.tech](https://api.voip.wrld.tech) — Backend API
- [wrld.host](https://wrld.host) — WRLD hosting platform
