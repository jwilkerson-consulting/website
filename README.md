# jwilkersonconsulting.com

Marketing site for **J. Wilkerson Consulting**, the consulting practice of Jerod W. Wilkerson.

Static site (plain HTML/CSS, no build step) hosted on GitHub Pages with a custom domain. Light theme, BYU Royal accent — a deliberate counterpart to the book site (agenticprogrammingbook.com).

© 2026 Jerod W. Wilkerson. All rights reserved. Site code and content are not licensed for reuse.

## Files

- `index.html` — the page (single landing page)
- `styles.css` — styles (light theme; BYU Royal `#0047BA`, Navy `#002E5D`)
- `favicon.svg` — favicon ("J." mark in the wordmark navy `#001A4D`)
- `images/` — author photo (200/400/600px) and the wordmark logo (`logo*.png` navy, `logo-white*.png` for dark backgrounds), sourced from `marketing/logos/`
- `CNAME` — custom domain for GitHub Pages (`jwilkersonconsulting.com`)
- `.nojekyll` — tells Pages to serve files as-is (no Jekyll processing)

## Preview locally

Open `index.html` in a browser, or serve the folder:

    python3 -m http.server 8000
    # then visit http://localhost:8000

## Deploy (GitHub Pages)

1. Push this folder to a public repo (no license).
2. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main` / `/ (root)`.
3. The custom domain is picked up automatically from `CNAME`.
4. Configure DNS at GoDaddy (see below).
5. Once DNS resolves, tick **Enforce HTTPS** (cert provisioning can take a few minutes up to ~an hour).

## DNS records (GoDaddy)

Add these at GoDaddy → **My Products → Domain → DNS**. (Reuses GitHub Pages' published IPs — same as the book site.)

Apex domain `jwilkersonconsulting.com` — four A records and four AAAA records pointing at GitHub Pages:

    A     @   185.199.108.153
    A     @   185.199.109.153
    A     @   185.199.110.153
    A     @   185.199.111.153
    AAAA  @   2606:50c0:8000::153
    AAAA  @   2606:50c0:8001::153
    AAAA  @   2606:50c0:8002::153
    AAAA  @   2606:50c0:8003::153

`www` subdomain — CNAME to the org's GitHub Pages host:

    CNAME  www   jwilkerson-consulting.github.io.

GoDaddy notes:
- If a default parked **A `@`** record exists, delete it before adding the four above.
- GoDaddy may show a default `CNAME www → @`; replace it with the CNAME above.
- Leave any unrelated records (email/MX, verification TXT) untouched.

## Notes / things to wire up later

- **Contact:** the CTA is a `mailto:` to `jerod.wilkerson@gmail.com`. Swap to a domain
  address (e.g. `jerod@jwilkersonconsulting.com`) if/when email is set up for the domain —
  it appears in `index.html` (three places) and the footer.
- **Social image:** add a share image to `images/` and uncomment the `og:image` meta tag.
