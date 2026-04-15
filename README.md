# AerialFrame Web Widgets

A collection of 11 beautiful web widgets designed to be embedded in [AerialFrame](https://aerialframe.app)'s WebView widget. Each widget is a single HTML file — just copy the URL and paste it into your widget settings.

**[Browse the gallery →](https://luigiinred.github.io/aerialframe-web-widgets/)**

---

## Quick Start

1. In AerialFrame, go to **Settings → Widgets → Add Widget → Web View**
2. Copy a widget URL from the table below
3. Paste it into the **URL** field in widget settings
4. Optionally set an **Auto-Refresh** interval (recommended for time-based widgets)

---

## Widgets

| Widget | Description | URL |
|--------|-------------|-----|
| **Minimal Clock** | Clean digital clock with date | `widgets/minimal-clock.html` |
| **Analog Clock** | SVG analog clock with smooth hands | `widgets/analog-clock.html` |
| **Inspirational Quotes** | 25 rotating quotes with crossfade | `widgets/quotes.html` |
| **Countdown Timer** | Days/hours/minutes to a target date | `widgets/countdown.html` |
| **World Clocks** | Multiple timezone clocks | `widgets/world-clocks.html` |
| **Gradient Orb** | Animated ambient gradient decoration | `widgets/gradient-orb.html` |
| **Daily Affirmations** | Rotating positive affirmations | `widgets/affirmations.html` |
| **Moon Phase** | Real-time moon phase & illumination | `widgets/moon-phase.html` |
| **Floating Particles** | Animated particle field with lines | `widgets/particles.html` |
| **Neon Text** | Glowing neon sign with custom text | `widgets/neon-text.html` |
| **Joke of the Day** | Random jokes from JokeAPI with punchline reveal | `widgets/joke.html` |

**Base URL:** `https://luigiinred.github.io/aerialframe-web-widgets/`

For example, to use the Minimal Clock:
```
https://luigiinred.github.io/aerialframe-web-widgets/widgets/minimal-clock.html
```

---

## Customization

Every widget supports URL parameters for customization. Add them to the URL with `?param=value&param2=value2`.

### Minimal Clock

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color (hex) |
| `24h` | `true` | Use 24-hour format (`true`/`false`) |
| `seconds` | `true` | Show seconds (`true`/`false`) |
| `date` | `true` | Show date below time (`true`/`false`) |

**Example:** `?color=%2364b5f6&24h=false&seconds=false`

### Analog Clock

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Clock face & hands color |
| `accent` | `#ff6b6b` | Second hand color |
| `seconds` | `true` | Show second hand |
| `numerals` | `true` | Show hour numerals |

**Example:** `?accent=%2300ff87&numerals=false`

### Inspirational Quotes

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `30` | Seconds between quotes |

**Example:** `?interval=60&color=%23e0e0e0`

### Countdown Timer

| Parameter | Default | Description |
|-----------|---------|-------------|
| `date` | `2025-12-31T00:00:00` | Target date (ISO 8601) |
| `title` | *(empty)* | Label above countdown |
| `color` | `#ffffff` | Text color |
| `accent` | `#64b5f6` | Progress ring color |
| `ring` | `true` | Show progress ring |

**Example:** `?date=2026-07-04T00:00:00&title=Independence%20Day&accent=%23ff6b35`

### World Clocks

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `24h` | `true` | Use 24-hour format |
| `cities` | *(4 defaults)* | JSON array of `{name, tz}` objects |

**Default cities:** New York, London, Tokyo, Sydney

**Custom cities example:**
```
?cities=[{"name":"Paris","tz":"Europe/Paris"},{"name":"Dubai","tz":"Asia/Dubai"}]
```
(URL-encode the JSON in practice)

### Gradient Orb

| Parameter | Default | Description |
|-----------|---------|-------------|
| `preset` | `aurora` | Color preset (see below) |
| `blur` | `40px` | Blur amount |
| `opacity` | `0.6` | Orb opacity (0–1) |
| `c1`–`c4` | *(from preset)* | Override individual colors |

**Presets:** `sunset`, `ocean`, `aurora`, `berry`, `forest`, `fire`, `lavender`, `neon`

**Example:** `?preset=sunset&opacity=0.8`

### Daily Affirmations

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `20` | Seconds between affirmations |

### Moon Phase

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |

### Floating Particles

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Particle color |
| `count` | `50` | Number of particles |
| `speed` | `0.5` | Movement speed |
| `size` | `3` | Max particle size (px) |
| `connect` | `120` | Line connection distance (px) |
| `lines` | `true` | Show connecting lines |

**Example:** `?count=80&color=%2300ff87&speed=0.3&lines=false`

### Neon Text

| Parameter | Default | Description |
|-----------|---------|-------------|
| `text` | `Hello` | Main text to display |
| `subtitle` | *(empty)* | Smaller text below |
| `preset` | `pink` | Color preset (see below) |
| `color` | *(from preset)* | Override glow color |
| `glow` | *(from preset)* | Override text fill color |
| `flicker` | `true` | Enable flicker animation |

**Presets:** `pink`, `blue`, `green`, `orange`, `purple`, `red`, `cyan`, `yellow`, `white`

**Example:** `?text=Welcome%20Home&subtitle=The%20Garrabrants&preset=blue&flicker=false`

### Now Playing Visualizer

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `accent` | `#1DB954` | Equalizer bar color |
| `title` | `Bohemian Rhapsody` | Track title |
| `artist` | `Queen` | Artist name |
| `album` | `A Night at the Opera` | Album name |
| `bars` | `8` | Number of equalizer bars |
| `disc` | `true` | Show spinning disc |

**Example:** `?title=Starman&artist=David%20Bowie&album=Ziggy%20Stardust&accent=%23ff6b35`

### Joke of the Day

Uses [JokeAPI](https://v2.jokeapi.dev/) (free, no auth). Two-part jokes show the setup first, then reveal the punchline after a delay. Falls back to built-in jokes if the API is unavailable.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `60` | Seconds between jokes |
| `category` | `Any` | Joke category: `Any`, `Programming`, `Pun`, `Misc`, `Dark`, `Spooky`, `Christmas` |
| `reveal` | `3` | Seconds before punchline appears (two-part jokes) |

**Example:** `?category=Programming&interval=45&reveal=5`

---

## Design Principles

All widgets follow these principles to work well as photo frame overlays:

- **Transparent backgrounds** — blend naturally over any photo
- **White text with shadow** — readable on both light and dark images
- **Responsive sizing** — adapt to any widget grid size
- **Self-contained** — single HTML file, no external dependencies
- **Configurable** — customize via URL parameters

---

## Hosting Your Own

These widgets are hosted for free via [GitHub Pages](https://pages.github.com/). You can also:

1. **Self-host**: Put the HTML files on any web server
2. **Local file server**: Use a simple local server for offline use
3. **Fork & customize**: Fork this repo, edit the widgets, and host your own version

---

## Creating Your Own Widgets

Want to make your own? Read **[BEST_PRACTICES.md](BEST_PRACTICES.md)** for the full guide on sizing, padding, and layout. Here's the starter template:

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
</style>
</head>
<body>
<div class="content">
  <div class="title" id="title">Widget</div>
</div>
<script>
  const params = new URLSearchParams(window.location.search);
  const color = params.get('color') || '#ffffff';
  document.documentElement.style.setProperty('--color', color);
</script>
</body>
</html>
```

**Key rules** (see [BEST_PRACTICES.md](BEST_PRACTICES.md) for details):
- **Edge-to-edge** — Use `padding: 4px` (fixed), never percentage padding
- **Size with `min()`** — `font-size: min(12vw, 10vh, 8rem)` scales with the smaller dimension
- **Transparent background** — `background: transparent` on html and body
- **Readable over photos** — `text-shadow` creates a halo for readability
- **No wrapping** — `white-space: nowrap` on single-line text
- **Self-contained** — No external CSS, JS, fonts, or APIs

---

## License

MIT — free to use, modify, and distribute.
