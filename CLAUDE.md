# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Quick Reference

**Project**: "Forget Me Not: The Human Cost of War" - Interactive D3.js "poppy field" visualization of global conflict casualties (1900-2025).

**Technology**: Single-file HTML with embedded CSS/JS, D3.js v7, Tailwind CSS 2.2.19 (CDN).

**Live URL**: https://dr.eamer.dev/datavis/forget_me_not/

**Parent Documentation**: See `/home/coolhand/html/datavis/CLAUDE.md` for full context.

## Commands

```bash
# Local development
python3 -m http.server 8000
# Open: http://localhost:8000/forget_me_not/
```

## Key File

- `index.html` - Complete application (embedded CSS/JS)

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

## Data Structure

Conflicts array in `initChart()`:
```javascript
{ "n": "Conflict Name", "s": 1939, "e": 1945, "d": 75000000, "r": "Europe" }
// n=name, s=start, e=end, d=deaths, r=region
```

## Key CSS Variables

```css
--bg-color: #f3efe6;
--header-color: #8b0000;
--flower-color: #779ecb;
--stem-color: #2e3b1f;
```

## Common Modifications

**Flower proportions**:
- Size scale: `rScale` (~line 697)
- Center circle: `Math.min(size * 0.22, 16)` (~line 868)
- White dot: `Math.min(size * 0.07, 5)` (~line 875)
- Petals: `petalSize = size * 0.45` (~line 834)

**Hover fade**: Opacity 0.35 (~line 876), transition 0.6s (~line 145)

## Tailwind Limitation

Using Tailwind CDN 2.2.19 (no JIT). Arbitrary values like `bg-[#hex]` won't work - use inline styles or CSS classes instead.

## Development

No build process. Edit `index.html` directly and refresh browser.
