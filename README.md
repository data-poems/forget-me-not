# FORGET ME NOT

120+ years of war casualties drawn as a poppy field. Each conflict becomes a forget-me-not flower — stem length shows duration, flower size encodes deaths. Scroll through history as wars bloom and fade, 1900-2025.

## Visual Encoding

| Element | Data Property | Scale |
|---------|--------------|-------|
| Stem span (arc) | Conflict duration | Linear (start → end year) |
| Flower height | Annual casualty rate | Log scale [500, 15M] |
| Flower size | Total deaths | Sqrt scale [0, 20M] → [18, 140]px |
| Center color | Geographic region | 5 categorical colors |
| Petal color | Forget-me-not blue | Fixed #779ecb |

## Region Colors

- Europe: #b91c1c (red)
- Asia: #d97706 (amber)
- Africa: #15803d (green)
- Middle East: #1d4ed8 (blue)
- Americas: #7e22ce (purple)

## Features

- **120+ conflicts**: Major wars with documented casualties
- **Horizontal timeline**: Scroll through 125 years of history
- **Interactive hover**: Click any flower for conflict details
- **Perceptual scaling**: Sqrt for area, log for rates
- **Accessible**: Keyboard navigation, screen reader support

## Technical Stack

- **D3.js v7**: SVG rendering and scales
- **Tailwind CSS 2.2.19**: Utility-first styling (CDN)
- **Vanilla JavaScript**: No frameworks
- **Playfair Display + Lato fonts**: Serif + sans-serif pairing

## Files

- `index.html` - Complete single-file application (48KB)
- `CLAUDE.md` - Development documentation
- `social-share.png` - Open Graph image (1009KB)

## Data Structure

Embedded in `initChart()`:
```javascript
{ "n": "Conflict Name", "s": 1939, "e": 1945, "d": 75000000, "r": "Europe" }
// n=name, s=start, e=end, d=deaths, r=region
```

## Local Development

```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

## Data Sources

Casualty estimates compiled from:
- Wikipedia List of Wars and Anthropogenic Disasters by Death Toll
- Uppsala Conflict Data Program (UCDP)
- Various historical sources and scholarly estimates

Note: Casualty figures for historical conflicts vary widely across sources. This visualization uses mid-range estimates.

## Author

Luke Steuber
https://lukesteuber.com
