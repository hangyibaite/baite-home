Here's what that component does and how to replicate it:

**What it does:** Splits text into words. As you scroll, each word fades from 20% to 100% opacity sequentially — creating a "reading" effect tied to scroll position.

Save this as `assets/reference/scroll-opacity-notes.md`:

```markdown
# Magic Text (Scroll-Reveal Words) — Vanilla Implementation

## What it does
- Text split into individual <span> words
- Each word has a ghost (opacity 0.2) and an active layer
- On scroll, words progressively fade to full opacity based on scroll progress through the container
- Start: when container top hits 90% of viewport
- End: when container top hits 25% of viewport

## HTML Structure
```html
<p class="magic-text" data-magic-text>
  <!-- JS will split this into spans automatically -->
  Your full text goes here as plain text.
</p>
```

## CSS
```css
.magic-text {
  display: flex;
  flex-wrap: wrap;
  line-height: 0.5;
  padding: 1rem;
}

.magic-word {
  position: relative;
  margin-top: 12px;
  margin-right: 0.25rem;
  font-size: 1.875rem;
  font-weight: 600;
}

.magic-word__ghost {
  opacity: 0.2;
}

.magic-word__active {
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
  transition: none; /* GSAP handles this */
}
```

## JS (GSAP ScrollTrigger)
```js
document.querySelectorAll('[data-magic-text]').forEach(container => {
  const text = container.textContent.trim();
  container.innerHTML = '';

  const words = text.split(/\s+/);

  words.forEach(word => {
    const span = document.createElement('span');
    span.className = 'magic-word';
    span.innerHTML = `
      <span class="magic-word__ghost">${word}</span>
      <span class="magic-word__active">${word}</span>
    `;
    container.appendChild(span);
  });

  const activeSpans = container.querySelectorAll('.magic-word__active');

  activeSpans.forEach((span, i) => {
    const start = i / words.length;
    const end = start + 1 / words.length;

    gsap.to(span, {
      opacity: 1,
      scrollTrigger: {
        trigger: container,
        start: 'top 90%',
        end: 'top 25%',
        scrub: true,
      },
      ease: 'none',
      // Map this word's progress to its range
      onUpdate: function() {
        const progress = this.scrollTrigger.progress;
        const wordOpacity = gsap.utils.mapRange(start, end, 0, 1, progress);
        span.style.opacity = gsap.utils.clamp(0, 1, wordOpacity);
      }
    });
  });
});
```

## Usage
Add `data-magic-text` attribute to any <p> element. JS auto-splits and animates.

## Best for
- Conviction section (the storytelling block)
- Subheading text
- Any editorial text that should feel like "reading along"
```

Tell Claude Code to use this pattern for your Conviction section instead of simple fade-in paragraphs. Paste this into Claude Code:

> When asked to implement mplement the magic-text scroll reveal pattern from assets/reference/scroll-opacity-notes.md. Each word should progressively fade from 20% to 100% opacity as the user scrolls through the text block. Use GSAP ScrollTrigger with scrub. Apply it to the full conviction copy.