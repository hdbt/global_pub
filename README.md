# global_pub

A GitHub-style animated globe that visualises worldwide academic publishing activity — much like GitHub's commit globe, but for scholarly papers.

## Features

- **Rotating 3D globe** — orthographic projection rendered on a pure HTML5 Canvas (no external libraries, no server required)
- **Animated arcs** — great-circle lines connecting publication origin to a simulated co-author country
- **Pulsing rings & glowing dots** — appear at each publication event
- **50 countries** weighted by real-world academic output (China, USA, UK, Germany, …)
- **20 research fields** colour-coded by domain (STEM/Computing, Medicine, Social Sciences, Arts & Humanities, Earth & Environment)
- **Live counter strip** — papers today, per-hour rate, countries active, events shown; anchored to the real-world figure of ~2.5 million scholarly articles per year
- **Side panel** — top publishing countries leaderboard, active fields breakdown, scrolling recent-publications feed
- **Speed slider** — slow to 0.2× or crank up to 5× for a lively view
- **Mouse/touch drag** — rotate the globe manually
- **Star background**, dark neon theme, atmospheric rim glow

## Usage

Just open `index.html` in any modern browser — no build step, no server, no internet connection required.

```
open index.html
```

Or serve it with any static web server:

```
python3 -m http.server
```
