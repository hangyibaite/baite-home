# Studio Namma Reference Notes

## Animation Patterns
- Word reveal: overflow-hidden wrapper per word, translateY(100%)→0%, stagger 0.02s
- Line reveal: overflow-hidden mask per line, translateY(110%)→0%, stagger 0.12s  
- Grow appear: scale(0.9)+opacity(0) → scale(1)+opacity(1) on scroll
- Simple appear: opacity(0)+translateY(3rem) → opacity(1)+translateY(0)
- Nav/link hover: dual-layer text swap (first/second) on hover

## Hero Mouse Follow
- Uses gsap.quickTo() for smooth cursor-lagged element
- Video element follows mouse with rotationX/Y based on velocity
- Scales up when idle (1.2), scales down to 1 when moving

## Smooth Scroll
- Lenis with lerp: 0.05, wheelMultiplier: 1
- Connected to GSAP ticker + ScrollTrigger.update()

## Custom Cursor
- 16px circle, follows mouse with 0.3 lerp
- Expands to labeled pill on [data-cursor-hover] elements
- data-cursor-hover="Label" sets the hover text

## Typography
- Headings use SplitText chars with yPercent: 150→9, stagger 0.027
- Mono text (labels) uses translateY(120%) + scale(0.9) reveal
- Anti-aliased: -webkit-font-smoothing + text-rendering: optimizeLegibility

## CSS Variables (theme system)
- --light: #e4e4e4, --dark: #111111
- --background and --text swap via data-theme attribute
- Transitions only during .theme-toggling class (prevents flash)

## Key Easings
- "custom": M0,0 C0.819,0.077 0,1 1,1 (snappy decel)
- "latestVisualAppear": overshoots slightly then settles
- All scroll triggers: start "top 95%", once: true


IMPORTANT: Note that this should be replicated with vanilla html/css/js NOT created with a react framework