# Atoll Reference Notes

## Animation Patterns to Replicate
- Sticky nav: white bg + backdrop-blur + bottom border appears on scroll
- Text reveal: lines animate in one by one (translateY + rotate 2deg, staggered)
- Section dividers: border-bottom animates width 0→100% on scroll enter
- Horizontal scroll section: cards slide left, sticky container
- 3D floating object: Three.js canvas, scroll-pinned, moves through page
- Image distortion: canvas overlay on hover (WebGL ripple effect)

## Typography System
- Headings: vw-based (e.g., 9.7vw for massive display, 3.3vw for h1, 2.2vw for h2)
- Body: ~0.97vw with tight tracking
- Uses fluid vw units everywhere, not clamp()

## Color
- bg: #E6E8EA (light gray)
- primary: #091423 (near-black navy)
- Clean, minimal, two-tone

IMPORTANT: Note that this should be replicated with vanilla html/css/js NOT created with a react framework