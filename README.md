# AIQ Studio

A two-page cinematic site for AIQ Studio — a private AI atelier in Dubai. One Brain, trained on one brand. Every creative discipline in one voice.

- `index.html` — the cinematic film (scroll-driven Three.js solar system)
- `studio.html` — the studio page (what we do, how, portfolio, contact, visit)
- `404.html` — friendly not-found page
- `robots.txt`, `sitemap.xml` — SEO
- `og-image.png` — 1200×630 social-share / link-preview card
- `logo.svg` — brand emblem (referenced by JSON-LD structured data)

## Stack

- Pure HTML / CSS / JS. No build step.
- Three.js (r160) loaded from unpkg.
- Google Fonts: Instrument Serif + DM Sans.
- WebAudio API for the salon-piano theme (user-gesture activated).

## Deploy

### Option A — GitHub Pages

1. Create a new public repository on GitHub.
2. Upload every file in this folder to the repository root, including:
   - `index.html`, `studio.html`, `404.html`
   - `robots.txt`, `sitemap.xml`
   - `og-image.png`, `logo.svg`
   - `README.md`
3. Go to **Settings → Pages**, set **Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Site is live at `https://<your-user>.github.io/<repo>/`.
5. To use a custom domain (e.g. `aiqstudio.ae`): add a `CNAME` file containing `aiqstudio.ae`, then point your DNS:
   - `A` records for the apex domain → GitHub Pages IPs (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153)
   - `CNAME` for `www` → `<your-user>.github.io`

### Option B — Netlify / Vercel

Drag-and-drop the folder onto Netlify Drop or import the repo in Vercel. Both auto-deploy and provide HTTPS + a free preview URL.

### Option C — Cloudflare Pages

Connect the GitHub repo. Build command: empty. Output directory: `/`. Done.

## Swap before launch

- **Contact details** — `hello@aiqstudio.ae` and the placeholder phone `+971 4 000 0000` appear in `studio.html` (contact section) and in the JSON-LD of both pages. Replace both with real details before launch.
- **Domain / URLs** — every absolute URL (canonical, Open Graph, Twitter, JSON-LD, `sitemap.xml`, `robots.txt`, and the `404.html` link) currently points to `https://ghuser03.github.io/Aiq-Studio-A/`, which is where the site is live now. If you move to a custom domain (e.g. `aiqstudio.ae`), find-and-replace that base URL across all files, then add a `CNAME` file (see Option A, step 5).
- **JSON-LD** — the `Organization` schema in both pages reflects the current entity, address and contact points; adjust if the legal entity differs.
- **Contact form** — wire the `<form>` submit in `studio.html` to a backend (Formspree, Resend, or your own endpoint). It currently validates client-side and shows a success state but does not transmit.

## Performance notes

- Both pages use `overflow-x: hidden` and 100vw clamping to guarantee no horizontal scroll on any device.
- Three.js renderer caps device pixel ratio at 1.5 on mobile (2 on desktop) and drops antialiasing on mobile. Procedural textures are generated smaller on mobile (1024² / 512²) than desktop (4096² / 2048²), sphere and ring geometry use lower segment counts on mobile, and particle counts are reduced (3,000 stars on mobile vs 14,000 on desktop; 120 dust vs 320).
- All fonts use `&display=swap` to avoid invisible-text flash.
- The only hosted image assets are `og-image.png` (link previews) and `logo.svg`; every in-page visual is procedural (Three.js textures, SVG, CSS). No CDN cost beyond fonts + Three.js.
- The landing-page 3D scene only renders while it is actually on screen (roughly the first and last 9% of the scroll). Through the long museum section in between, the GPU render and all 3D scene updates are skipped entirely.

## Accessibility

- Semantic landmarks (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`).
- Form has proper labels, `autocomplete` hints, ARIA `aria-live` status messages.
- Color contrast meets WCAG AA on the dominant text/background combinations.
- `prefers-reduced-motion` is respected for the most aggressive animations via the existing visibility-change pauses; consider adding a stricter override if you find motion-sensitive users complain.

## Browser support

Modern evergreen browsers (Chrome / Edge / Safari / Firefox, last 2 years). The cinematic 3D requires WebGL2 — the site degrades gracefully if WebGL is unavailable (canvas stays empty, text content still reads).

## License

All content © 2026 AIQ Studio. Public-domain typography (Instrument Serif, DM Sans) and Three.js (MIT license) used as dependencies.
