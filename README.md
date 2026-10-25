# Life Field

Conway's Game of Life on an unbounded field. It is a static site: `index.html` plus `presets.json`, with no build step.

## Deploy to Cloudflare Pages

**Dashboard upload:** Workers & Pages → Create → Pages → Upload assets. Drop this folder or the zip.

**GitLab:** Push this folder to a repo, then go to Workers & Pages → Create → Pages → Connect to Git → GitLab. Use these settings:
- Framework preset: None
- Build command: (empty)
- Build output directory: `/`

Every push to the production branch redeploys.

## Run locally

`fetch()` doesn't work over `file://`, so serve the folder:

```
python -m http.server 8000
```

## Adding presets

Append an entry to `presets` in `presets.json`:

```json
{
  "name": "Copperhead",
  "category": "Spaceships",
  "meta": "c/10 orthogonal · 2016",
  "description": "Optional one-liner shown under the name.",
  "rle": "b2o2b2o$3b2o$3b2o$obo2bobo$o6bo2$o6bo$b2o2b2o$2b4o2$3b2o$3b2o!"
}
```

| Field | Required | Notes |
|---|---|---|
| `name` | yes | |
| `rle` or `cells` | yes | `rle`: standard RLE body (header and `#` lines are ignored, so whole LifeWiki files work). `cells`: array of strings, `O` = alive, `.` = dead |
| `category` | no | Groups the list; categories appear in first-seen order |
| `meta` | no | Short mono line (period, speed, discoverer) |
| `description` | no | |
| `featured` | no | `true` loads and runs this preset on page open |

RLE for almost any pattern is on its LifeWiki page. To capture something you drew in the app, use **Export**.

## Controls

Space play/pause · N step · F fit · G grid · D toggle draw tool · drag to pan · scroll or pinch to zoom · click to toggle a cell
