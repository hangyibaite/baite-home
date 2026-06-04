# Session Summary — Baite Studio / home.html

## File
Single-file site: `home.html` — all CSS in `<style>`, all JS in `<script type="module">` before `</body>`.
Serve with `npx serve .` (GLB model requires HTTP, not file://).

---

## Sections Built (in DOM order)

### NAV
- Fixed, glassmorphism on scroll (`.nav.scrolled`)
- Button: "Apply Now" → `.btn-primary` (black bg, orange slide-in on hover)

### HERO (`#hero`)
- `.social-proof-pill` — absolute, `top: 68px`, scales to `0.72` on mobile (`top: 44px`)
- Headline: `TURN YOUR CONTENT INTO CASH` + inline `.sticker-btn` (image bg → orange slide-in hover, black on hover, word-wrap reveal animation)
- Three.js fluffball: `assets/images/fluffball.glb`, scale `4.0`, `ghost.position.y = -0.35`, DRACOLoader
- Fish cursor on hero hover: `data:` SVG emoji URI
- Coin/SVG cursor trail on **conviction** section only (`assets/images/2.svg`, `3.svg`, `4.svg`)
- Marquee: `position: absolute; bottom: -30px` inside hero, overlaps cat bottom

### FEATURES (`.features`, dark `#1A1A1A`)
- Canvas grid distortion (cursor pushes grid lines)
- SVG displacement filter on heading (`#text-distort-filter`)
- 6 glass cards: 2-col desktop / 1-col mobile, 3D tilt + glare spotlight via `--mouse-x/y`
- **No `backdrop-filter`** — it makes cards opaque and blocks canvas

### CONVICTION (`#conviction`)
- Magic-text scroll reveal: single ScrollTrigger on `.conviction`, one shared progress across all 4 paragraphs sequentially
- `start: 'top 75%'`, `end: 'center 5%'`, `scrub: 0.2`
- Ends with centred `.conviction-cta` "Apply Now" button (black, orange slide-in, `4px` border, `clamp(1.5rem…)`)
- Cursor trail active here

### TESTIMONIALS (`.testimonials`, black bg)
- CSS marquee, 5 cards × 2 sets, `testi-scroll 36s linear infinite`
- White border lines on `.testimonials-track-wrapper`
- No pause on hover

### CTA EDITORIAL (`.cta-editorial`, black bg, `min-height: 95vh`)
- Two text chunks: `.cta-headline` (huge, `clamp(2rem, 7.5vw, 7rem)`) + `.cta-sub` (white, `max-width: 56ch`)
- 3D tilt button `#cta-3d-btn`: orange `#EA6200`, white `3px` border, 16-layer stacked black extrusion shadow, orange ambient glow
- Resting state: `rotateX(8deg) rotateY(-8deg) translateZ(30px) scale(2.04)` — responsive via `getScale()` (1.1 / 1.4 / 2.04)
- `mousemove`: transition none, live tilt; `mouseleave`: 0.5s snap-back

---

## Key CSS Classes / Patterns

| Class | Notes |
|---|---|
| `.btn-primary` | Orange bg, `::before` black slide-in left→right |
| `.nav .btn-primary`, `.conviction-cta .btn-primary` | Black bg, orange slide-in |
| `.sticker-btn` | Inline pill in headline, image bg, orange slide-in, black border |
| `.word-wrap / .word-inner` | GSAP hero text reveal (translateY 105%→0%) |
| `.magic-word / .magic-word__ghost / __active` | Conviction scroll opacity reveal |
| `.feat-card` | No `backdrop-filter` — critical for canvas grid visibility |
| `.cta-3d-btn` | 3D extruded button, JS-driven tilt, stacked box-shadow |
| `.social-proof-pill` | Absolute in hero, mobile scale(0.72) at top: 44px |

---

## Pending / Not Built
- Section 7: CTA Float (Atoll-inspired floating container) — not started
- Section 8: Footer — not started
- Testimonial real content (names, photos, quotes) — placeholders only
- Pain → Solution section — skipped/not in build queue

---

## CDN Libraries
```html
gsap@3.12, ScrollTrigger, Lenis@1.1
Three.js @0.160 (importmap, module script)
GLTFLoader + DRACOLoader (jsm)
Google Fonts: Manrope 400/500/600/700/800
```

## Assets
- `assets/images/fluffball.glb` — 3D cat model
- `assets/images/hero-button-image.png` — sticker button base image
- `assets/images/2.svg`, `3.svg`, `4.svg` — cursor trail icons
- `assets/images/fish.svg` — hero fish cursor (1.5MB, too large to inline; emoji fallback used)
