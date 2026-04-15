# Best Practices for AerialFrame Web Widgets

Follow these guidelines to build widgets that look great at every size — from a tiny 2×2 corner widget to a large 6×5 panel.

---

## 1. Go Edge-to-Edge

Widgets are embedded inside a grid cell that may already have its own padding and background treatment from AerialFrame. Your widget should fill every available pixel.

**Do:** Use a tiny fixed padding (4–6px) as a safety margin to prevent clipping.

```css
body { padding: 4px; }
```

**Don't:** Use percentage-based padding. `padding: 8%` eats 16% of the width — on a 200px widget that's 32px wasted on each axis.

```css
/* BAD — shrinks content at small sizes */
body { padding: 5%; }
body { padding: 8%; }
```

---

## 2. Size Text with `min()`, Not `clamp()`

`clamp(min, preferred, max)` seems right, but the `min` floor is often too large for small widgets or too small to matter. Instead, use `min()` with both `vw` *and* `vh` units so text scales with whichever dimension is smaller. This prevents text from overflowing when the widget is tall-and-narrow or wide-and-short.

**Do:**

```css
.time {
  font-size: min(12vw, 10vh, 8rem);
}
```

This picks the smallest of: 12% of width, 10% of height, or 8rem — so the text always fits.

**Don't:**

```css
/* BAD — only scales with width, ignores height */
.time {
  font-size: clamp(2rem, 12vw, 8rem);
}
```

### Why both `vw` and `vh`?

A widget might be placed in a 4×2 grid cell (wide and short) or a 2×4 cell (narrow and tall). Using only `vw` means text overflows vertically in short widgets. Using only `vh` means text overflows horizontally in narrow widgets. `min(vw, vh, max)` handles both.

---

## 3. Prevent Text Wrapping

When a widget shrinks, multi-word text wraps to a second line, which pushes content out of view. Use `white-space: nowrap` on single-line elements like clock times, labels, and titles.

```css
.time {
  white-space: nowrap;
}
```

For multi-line text (quotes, affirmations), let wrapping happen naturally but size the font using both `vw` and `vh` so lines fit.

---

## 4. Use Transparent Backgrounds

AerialFrame's WebView renders on top of photos. The widget blends into the photo when the background is transparent. A solid background blocks the photo underneath.

```css
html, body {
  background: transparent;
}
```

---

## 5. Design for Readability Over Photos

White text vanishes on light photos. Dark text vanishes on dark photos. Use text shadows to create a subtle halo that makes text readable on any image.

```css
.text {
  color: white;
  text-shadow: 0 1px 8px rgba(0,0,0,0.5);
}
```

For elements that need stronger contrast (small labels, thin fonts), increase the shadow spread:

```css
.small-label {
  text-shadow: 0 1px 4px rgba(0,0,0,0.6), 0 0 12px rgba(0,0,0,0.3);
}
```

---

## 6. Use `min()` for Non-Text Sizing Too

Apply the same `min(vw, vh, max)` pattern to icons, decorative elements, gaps, and other sized elements:

```css
.icon {
  width: min(10vw, 10vh, 80px);
  height: min(10vw, 10vh, 80px);
}

.gap {
  gap: min(3vw, 3vh, 2rem);
}
```

---

## 7. Make Everything Configurable via URL Parameters

Users paste a URL into AerialFrame's WebView settings — that's their only way to configure the widget. Use URL parameters for all customization.

```js
const params = new URLSearchParams(window.location.search);
const color = params.get('color') || '#ffffff';
const interval = parseInt(params.get('interval') || '30');
```

Common parameters every widget should support:

| Parameter | Purpose |
|-----------|---------|
| `color` | Primary text color (hex, e.g. `%23ffffff`) |

Provide sensible defaults for every parameter so the widget works with a bare URL.

---

## 8. Stay Self-Contained

No external CSS, JS, fonts, or API calls. Everything in one HTML file. This ensures:

- The widget loads instantly (no network round trips)
- It works offline
- There are no CORS issues in the WebView
- No third-party dependencies can break it

---

## 9. Prevent Scrolling and Overflow

The WebView disables scrolling, but content that overflows its bounds gets clipped silently. Lock down overflow:

```css
html, body {
  overflow: hidden;
}
```

---

## 10. Full Starter Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html, body {
    width: 100%; height: 100%;
    background: transparent;
    overflow: hidden;
    font-family: -apple-system, sans-serif;
    -webkit-font-smoothing: antialiased;
  }
  body {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 4px;
  }
  .content {
    text-align: center;
    color: var(--color);
    text-shadow: 0 1px 8px rgba(0,0,0,0.5);
    width: 100%;
  }
  .title {
    font-size: min(8vw, 8vh, 4rem);
    font-weight: 300;
    white-space: nowrap;
  }
  .subtitle {
    font-size: min(3vw, 3vh, 1.2rem);
    opacity: 0.6;
    margin-top: 0.3em;
  }
</style>
</head>
<body>
<div class="content">
  <div class="title" id="title">Widget</div>
  <div class="subtitle" id="subtitle">Subtitle</div>
</div>
<script>
  const params = new URLSearchParams(window.location.search);
  const color = params.get('color') || '#ffffff';
  document.documentElement.style.setProperty('--color', color);
</script>
</body>
</html>
```

---

## Quick Checklist

- [ ] Body padding is ≤ 6px (fixed, not percentage)
- [ ] Font sizes use `min(Xvw, Yvh, max)` — never just `vw` alone
- [ ] Single-line text has `white-space: nowrap`
- [ ] `background: transparent` on html and body
- [ ] Text has `text-shadow` for photo readability
- [ ] Decorative elements also use `min(vw, vh, max)` sizing
- [ ] All config is via URL parameters with defaults
- [ ] No external dependencies (CSS, JS, fonts, APIs)
- [ ] `overflow: hidden` on html and body
- [ ] Widget fills its container edge-to-edge
