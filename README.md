# AerialFrame Web Widgets

A collection of 22 web widgets designed to be embedded in [AerialFrame](https://aerialframe.app)'s WebView widget. Each widget is a single HTML file — just copy the URL and paste it into your widget settings.

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
| **Now Playing** | Decorative now-playing with disc and equalizer | `widgets/now-playing.html` |
| **Joke of the Day** | Random jokes from JokeAPI with punchline reveal | `widgets/joke.html` |
| **Random Facts** | Rotating "did you know?" facts | `widgets/random-facts.html` |
| **ISS Tracker** | Live ISS position on a mini world map | `widgets/iss-tracker.html` |
| **People in Space** | Who is currently in orbit, by spacecraft | `widgets/people-in-space.html` |
| **Trivia Questions** | Trivia with delayed answer reveal | `widgets/trivia.html` |
| **Daily Advice** | Random life advice from Advice Slip API | `widgets/daily-advice.html` |
| **Dog of the Day** | Random dog photos, filterable by breed | `widgets/dog-of-the-day.html` |
| **Hacker News** | Top headlines with scores and timestamps | `widgets/hacker-news.html` |
| **Sunrise & Sunset** | Today's sun times with a visual arc | `widgets/sunrise-sunset.html` |
| **Currency Exchange** | Live exchange rates from ECB | `widgets/currency.html` |
| **Cat Facts** | Random cat facts on a timer | `widgets/cat-facts.html` |

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

### Random Facts

Uses [Useless Facts API](https://uselessfacts.jsph.pl/) (free, no auth). Falls back to built-in facts offline.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `30` | Seconds between facts |

### ISS Tracker

Uses [Open Notify API](http://open-notify.org/) (free, no auth). Shows the live ISS position on a simplified world map.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `accent` | `#4fc3f7` | ISS dot and ping color |

### People in Space

Uses [Open Notify API](http://open-notify.org/) (free, no auth). Shows astronauts grouped by spacecraft.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |

### Trivia Questions

Uses [Open Trivia DB](https://opentdb.com/) (free, no auth). Shows a question, then reveals the answer after a delay.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `accent` | `#81c784` | Answer text color |
| `interval` | `30` | Seconds between questions |
| `reveal` | `5` | Seconds before answer appears |
| `category` | *(any)* | Category ID ([see list](https://opentdb.com/api_category.php)) |

**Example:** `?category=18&interval=20` (Computer Science trivia)

### Daily Advice

Uses [Advice Slip API](https://api.adviceslip.com/) (free, no auth). Falls back to built-in advice offline.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `45` | Seconds between advice |

### Dog of the Day

Uses [Dog CEO API](https://dog.ceo/dog-api/) (free, no auth). Shows a random dog photo that fills the widget.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Breed label color |
| `breed` | *(random)* | Filter by breed (e.g. `labrador`, `poodle/standard`) |
| `interval` | `30` | Seconds between photos |

**Example:** `?breed=corgi&interval=20`

### Hacker News

Uses [Hacker News API](https://github.com/HackerNews/API) (free, no auth, no limits).

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `accent` | `#ff6600` | Y logo color |
| `count` | `5` | Number of headlines |
| `feed` | `top` | Feed type: `top`, `new`, or `best` |

**Example:** `?feed=best&count=3`

### Sunrise & Sunset

Uses [Sunrise-Sunset API](https://sunrise-sunset.org/api) (free, no auth). Shows a sun arc with current position.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `lat` | `40.7128` | Latitude |
| `lng` | `-74.0060` | Longitude |

**Example:** `?lat=34.0522&lng=-118.2437` (Los Angeles)

### Currency Exchange

Uses [Frankfurter API](https://frankfurter.dev/) (free, no auth, ECB data).

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `base` | `USD` | Base currency code |
| `symbols` | `EUR,GBP,JPY,CAD` | Comma-separated target currencies |

**Example:** `?base=EUR&symbols=USD,GBP,CHF,SEK`

### Cat Facts

Uses [Cat Facts API](https://catfact.ninja/) (free, no auth). Falls back to built-in facts offline.

| Parameter | Default | Description |
|-----------|---------|-------------|
| `color` | `#ffffff` | Text color |
| `interval` | `30` | Seconds between facts |

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
    text-shadow:
      -1px 0 0 rgba(0,0,0,0.6),
      1px 0 0 rgba(0,0,0,0.6),
      0 -1px 0 rgba(0,0,0,0.6),
      0 1px 0 rgba(0,0,0,0.6),
      1px 2px 4px rgba(0,0,0,0.35);
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
