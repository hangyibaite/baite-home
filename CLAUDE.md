CLAUDE.md
PROJECT

Site: Baite Studio
Purpose: Course landing page + lead generation funnel
Stack: Plain HTML + CSS + Vanilla JavaScript (single page, no frameworks)
Goal: Capture email (nurture sequence) → sell course: Content to Cashflow Academy (hosted on Skool)
Tone: Premium designer studio meets warm personal brand — clean, bold, editorial, but never cold. Think Atoll Digital crossed with a high-end creator brand.


PRE-BUILD CHECKLIST (run before writing any code)

Read every file in .claude/skills/ — internalize all design rules, component patterns, and constraints before generating a single line of code.
Open and study every file in assets/reference/ — match the visual direction, layout density, spacing, typography scale, and color treatment shown.
If a skill or reference conflicts with this file, clarify with the user if you do not have sufficient context. If the user dismisses any questions, assume this file wins the conflict.
Before building any section: check in with the user on any placeholders, uncertain design decisions, missing assets, or ambiguous copy. Do not guess — ask.


STRUCTURE
/
├── CLAUDE.md
├── index.html              ← the entire site lives here
├── .gitignore
├── .git/
├── .claude/
│   └── skills/
└── assets/
    ├── images/
    ├── icons/
    └── reference/
Everything in one file. All CSS in a <style> tag in <head>. All JS in a <script> tag before </body>. No external CSS or JS files unless they are CDN libraries.

BUILD RULES

One section at a time. Stop after each section for review. Never output the entire site without explicit prior instruction.
Ask before assuming. If any copy, asset, interaction, or design detail is not explicitly defined in this file, ask the user before building. Do not fill in blanks silently.
Plain HTML/CSS/JS only. No React, no Next.js, no Vue, no Tailwind, no build tools, no npm.
All CSS goes inside <style> in <head>. Use CSS custom properties for theming.
All JS goes inside <script> before </body>.
External libraries allowed via CDN only:

GSAP + ScrollTrigger + SplitText (for scroll animations, text reveals): https://cdn.jsdelivr.net/npm/gsap@3/dist/
Lenis (smooth scroll): https://cdn.jsdelivr.net/npm/lenis@1/dist/lenis.min.js
Three.js (for 3D ghost model): https://cdn.jsdelivr.net/npm/three@0.160/build/three.module.js
Google Fonts (Manrope): <link> in <head>


No lorem ipsum. Use the exact copy provided below. Where copy is not yet provided, use an HTML comment <!-- PLACEHOLDER: [describe] — ask user --> and a visible placeholder in the UI.
Mobile responsive: 515px → 768px → 1440px. Design mobile-first with @media queries.
All images use placeholder <div> elements with descriptive labels until real assets are provided.
Prefer clamp() for fluid typography rather than breakpoint jumps.
GlassCard style: Do NOT create until the user pastes the specific 21st.dev glassmorphism CSS they want. Ask for it when the Features section is next in the build queue.
To preview: just open index.html in the browser. No dev server needed.


BRAND PALETTE
css:root {
  --bg:           #F5F5F0;
  --bg-elevated:  #FFFFFF;
  --bg-contrast:  #1A1A1A;
  --accent:       #1A1A1A;
  --accent-2:     #7A1B2D;
  --text:         #1A1A1A;
  --text-dim:     #444444;
  --text-inverse: #F5F5F0;
  --border:       rgba(0, 0, 0, 0.08);
  --border-glass: rgba(255, 255, 255, 0.18);
  --glass-bg:     rgba(255, 255, 255, 0.06);
}

TYPOGRAPHY

Font: Manrope via Google Fonts CDN
Headings: weight 700–800, letter-spacing: -0.03em, line-height: 0.92

Hero: clamp(2.5rem, 8vw, 6rem)
Sections: clamp(2rem, 5vw, 4rem)


Body: weight 400–500, line-height: 1.45, size clamp(1rem, 1.2vw, 1.15rem)
Load via:

html<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">

COMPONENTS (CSS classes, not framework components)
.btn-primary

bg: var(--accent), color: white, font-weight 600, border-radius 60px, padding 16px 40px
box-shadow: 0 2px 12px rgba(0,0,0,0.12)
Hover: scale(1.03), translateY(-2px), shadow deepens, transition 0.3s ease
Active: scale(0.98)

.btn-ghost

bg: transparent, 1px solid var(--border), color: var(--text)
Hover: bg rgba(0,0,0,0.04), border darkens

.glass-card

⚠️ DO NOT BUILD YET. User will paste the specific CSS. Use a simple white card with border-radius 24px and subtle border as placeholder.

.avatar-stack

5–6 overlapping circles, 36px, -8px margin overlap
2px solid var(--bg-elevated) border ring
Followed by: "Join 250+ creators already inside"

3D Ghost (Hero)

Three.js canvas rendering the GLB model at assets/images/ghost.glb
Positioned below CTA button and avatar stack, centered
Large (roughly 300–400px tall)
Smoothly tracks cursor — rotates toward mouse position using lerp in animation loop


ANIMATIONS (GSAP + CSS)
Global

Scroll reveal: GSAP ScrollTrigger — fade-up (opacity 0→1, translateY 32px→0, 0.7s ease-out) at 15% threshold
Stagger: 0.12s delay increments per child element
Smooth scroll: Lenis via CDN
Text reveal: GSAP SplitText — words in overflow-hidden wrappers, translateY(100%)→0%, stagger 0.02s

Cursor Effects

Features section: cursor trail — small images spawn at cursor, max 8, fade after 1.2s

Micro-Interactions (CSS only)

Cards: tilt on hover via CSS perspective + rotateX/Y
Links: underline slides in from left
Section transitions: subtle parallax (0.05–0.1 rate)


SECTIONS (build in this order)

Section 1 — Hero

Centered, full viewport height, generous whitespace
Massive headline → subheadline → "Apply Now" CTA button → avatar stack
3D ghost model below avatar stack, tracks cursor

Section 2 — Carousel

Full-bleed horizontal auto-scroll strip
Pills: "Content Strategy", "Funnel Building", "Email Sequences", "Community Growth", "Monetization", "Branding", "Paid Ads", "Course Creation"
CSS infinite scroll animation, pause on hover
No CTA

Section 3 — Conviction

Centered, max-width 680px, editorial text block
Scroll-triggered paragraph reveals (GSAP)
Ends with CTA button (label TBD — ask user)

Section 4 — Features

"Six things we build for you."
6 cards, 2-col desktop / 1-col mobile
Ask user for glass card style before building
Cursor trail active, staggered entrance, tilt-on-hover

Section 5 — Pain → Solution

Copy TBD — ask user

Section 6 — Testimonials

Placeholder cards — ask user for content

Section 7 — CTA Float

Full-viewport, centered
Floating container (Atoll-inspired), clickable → #community
Consider dark bg — ask user
Headline TBD — ask user

Section 8 — Footer

Simple: © 2025 Baite Studio · Privacy · Terms · social icons


COPY (final — use verbatim)
Hero
Headline: Turn your content into cash.
Subheadline: For creators who are done watching other people monetize the same audience they have.
CTA: Apply Now
Subheading
You don't need more followers, dear. You need a system that catches the attention you're already getting and turns it into revenue.
Conviction
You ever notice how your comments sound like love letters? "This changed my life." "OMG I love you… please never stop." "You're so underrated." And yet, somehow, despite all that spicy love, the people writing those comments are not exactly rushing to send you money.
Which is wild because honestly, they want to.
They're dying to see you succeed.
They just don't have a clear path from "I love this guy sm" to "here's my credit card," and so most of them watch your stuff for free forever and feel amazing about it. Bloody freeloaders (cough).
Not your fault, but... kinda your problem, ngl.
The thing is, it's not your content. (that shit's great, btw) It's just about everything that happens after the view, which is where you actually turn these followers into money. That just isn't there yet. And if you want to finally start printing cash from your content… you already know what to do. Hit the DAMN button👇
Features
Section Heading: Six things we build for you.
Card 1 — The Offer Engineer
An offer people line up to pay for, with an ascension ladder to scale LTV above it.
Card 2 — The Inbound Engine
Lead magnets, funnels, VSLs, nurture sequences, and the community that turns attention into booked calls.
Card 3 — The Bot Army
Manychat flows and automated DMs that run your front-end while you sleep.
Card 4 — The Detective Trackers
GA4, Meta Pixel, and full attribution so every dollar is traceable to its source.
Card 5 — The AI Machine ⭐
Wire AI into every layer so the whole thing builds, runs, and scales itself.
Card 6 — The Closing Room
The booking flow and call structure to convert without being weird about it.
Pain → Solution
<!-- PLACEHOLDER: ask user for specific pain/solution copy -->
Testimonials
<!-- PLACEHOLDER: ask user for testimonial quotes, names, and roles -->
CTA Section
<!-- PLACEHOLDER: ask user for final CTA headline and supporting text -->

CDN LIBRARIES (add to index.html)
html<!-- In <head> -->
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">

<!-- Before </body> -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12/dist/ScrollTrigger.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/lenis@1.1/dist/lenis.min.js"></script>
Add Three.js only when building the hero ghost model. Add SplitText only when building text animations.

GITIGNORE
.DS_Store
node_modules/
.env
*.log

REMINDERS

This is a premium brand. Every pixel matters. Generous whitespace, oversized type, intentional animation. Never cluttered.
The site tells a story: hook (Hero) → tease breadth (Carousel) → build conviction (Conviction) → prove depth (Features) → empathize + solve (Pain/Solution) → validate (Testimonials) → convert (CTA).
Performance: Lazy-load below-fold images, defer non-critical JS.
Accessibility: keyboard-navigable, proper heading hierarchy (h1 once in Hero), alt text, 4.5:1 contrast.
When in doubt, ask. Do not silently fill in missing information.
To preview: Open index.html directly in the browser, or use npx serve . for a local server.