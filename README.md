# Global Academic Publishing — Live Map

An interactive, real-time globe visualization of academic publications worldwide. Each dot that appears on the spinning globe represents a newly indexed research paper, streamed live from the [OpenAlex](https://openalex.org/) public API.

![Globe visualization showing research publication events as glowing dots on a dark world map](preview.png)

## Features

- **Live feed** — polls the OpenAlex API every 25 seconds for newly indexed works and drip-feeds them onto the globe one by one.
- **Orthographic globe** — smooth, canvas-rendered 3-D projection with hand-crafted land outlines and animated publication arcs.
- **Research domain colours** — each publication is colour-coded by field:
  | Colour | Domain |
  |--------|--------|
  | 🔵 Cyan `#00d4ff` | STEM / Computing |
  | 🟣 Purple `#a855f7` | Medicine / Health |
  | 🟢 Green `#22c55e` | Social Sciences |
  | 🟡 Amber `#f59e0b` | Arts & Humanities |
  | 🔴 Red `#ef4444` | Earth & Environment |
- **Side panel** — live-updating lists of top publishing countries, top disciplines, and the most recent paper titles.
- **Counter strip** — shows events seen today, active countries, total events shown, and the current replay-queue depth.
- **Pause / Resume** — freeze the feed at any moment without losing queued events.
- **Drag to rotate** — click-drag (or touch-drag) to spin the globe to any region.
- **Scroll to zoom** — mouse wheel (or pinch) zooms from 0.4× to 3×.
- **Hover tooltip** — hover over any glowing dot to see the paper title, country, field, and publication year.
- **Aggregate statistics** — country rankings and discipline breakdown are fetched from the OpenAlex `group_by` API on load, with automatic fallback to local JSON files.

## Usage

Just open `index.html` in any modern browser — no build step or server required. An internet connection is needed only for streaming live data from OpenAlex.

```
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

## Project Structure

```
global_pub/
├── index.html                  # Entire application (~1,300 lines, no dependencies)
├── data/
│   ├── country_rankings.json   # Fallback country publication counts
│   └── discipline_breakdown.json  # Fallback discipline breakdown
└── README.md
```

## Data Source

All live data comes from the free [OpenAlex REST API](https://docs.openalex.org/). No API key is required.

| Endpoint | Purpose |
|----------|---------|
| `/works?sort=publication_date:desc` | Stream of the most recently indexed papers |
| `/works?group_by=authorships.institutions.country_code` | Country-level publication totals |
| `/works?group_by=primary_topic.field.display_name` | Discipline breakdown |

## Configurable Constants

The following constants near the top of the `<script>` block can be tuned:

| Constant | Default | Description |
|----------|---------|-------------|
| `LIVE_MODE` | `true` | Toggle live OpenAlex polling on/off |
| `POLL_INTERVAL_MS` | `25000` | How often (ms) to poll for new works |
| `REPLAY_INTERVAL_MS` | `1500` | Delay (ms) between drip-fed globe events |
| `INITIAL_FETCH_SIZE` | `200` | Number of works fetched on the very first poll |
| `MAX_REPLAY_SKIP` | `5` | Max works to skip per tick when no country coords are found |
| `ZOOM_MIN` / `ZOOM_MAX` | `0.4` / `3.0` | Zoom range |

## Keyboard & Mouse Controls

| Action | Control |
|--------|---------|
| Rotate globe | Click-drag or touch-drag |
| Zoom | Mouse wheel or pinch |
| Pause / Resume feed | Click **⏸ Pause** button |
| Inspect a publication | Hover over a glowing dot |

## Credits

Publication data provided by [OpenAlex](https://openalex.org/) — a free and open catalogue of the global research system.