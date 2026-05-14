# AIQ Studio

A two-page cinematic site for AIQ Studio — a private AI atelier in Dubai. One Brain, trained on one brand. Every creative discipline in one voice.

- `index.html` — the cinematic film (scroll-driven Three.js solar system)
- `studio.html` — the studio page (what we do, how, portfolio, contact, visit)
- `404.html` — friendly not-found page
- `robots.txt`, `sitemap.xml` — SEO

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

- `[CONTACT_EMAIL]` / `hello@aiqstudio.ae` and `[CONTACT_PHONE]` / `+971 4 000 0000` in `studio.html` — replace with real details.
- The canonical URL `aiqstudio.ae` in meta tags — replace with your real domain.
- `JSON-LD Organization` schema in both pages — adjust if the legal entity is different.
- Contact form — wire `<form>` submit to a backend (Formspree, Resend, or your own endpoint). Currently the form validates client-side and shows a success state but doesn't transmit.

## Performance notes

- Both pages use `overflow-x: hidden` and 100vw clamping to guarantee no horizontal scroll on any device.
- Three.js renderer caps device pixel ratio at 1.25 on mobile (1.75 desktop), drops antialiasing on mobile, and reduces particle counts (4,500 stars + 120 dust on mobile, 14,000 + 320 on desktop).
- All fonts use `&display=swap` to avoid invisible-text flash.
- No images are hosted on the site — all visuals are procedural (Three.js textures, SVG, CSS). No CDN cost beyond fonts + Three.js.

## Accessibility

- Semantic landmarks (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`).
- Form has proper labels, `autocomplete` hints, ARIA `aria-live` status messages.
- Color contrast meets WCAG AA on the dominant text/background combinations.
- `prefers-reduced-motion` is respected for the most aggressive animations via the existing visibility-change pauses; consider adding a stricter override if you find motion-sensitive users complain.

## Browser support

Modern evergreen browsers (Chrome / Edge / Safari / Firefox, last 2 years). The cinematic 3D requires WebGL2 — the site degrades gracefully if WebGL is unavailable (canvas stays empty, text content still reads).

## License

All content © 2026 AIQ Studio. Public-domain typography (Instrument Serif, DM Sans) and Three.js (MIT license) used as dependencies.
