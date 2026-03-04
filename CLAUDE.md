# Sequoia Precision Components — Website

## Overview
Static single-page marketing website for Sequoia Precision Components (formerly Sequoia Automatic). Precision CNC machining for automotive and data center thermal management. No build system — single `index.html` with inline CSS/JS.

## Architecture
- **Single file**: `index.html` contains all HTML, CSS (in `<style>`), and JS (in `<script>`)
- **No framework/bundler** — pure HTML/CSS/JS, served by Nginx
- **Fonts**: Google Fonts (DM Sans + JetBrains Mono)
- **Responsive**: Mobile-first breakpoints at 768px and 1024px

## Serving
Currently served via standalone Docker container on port 8081:
```
docker run -d --name sequoia-website -p 8081:80 \
  -v /home/js/sequoia/sequoia-website:/usr/share/nginx/html:ro \
  --restart unless-stopped nginx:alpine
```
Not yet integrated into ai-stack/Traefik. When ready for production, add as an Nginx service in `~/ai-stack/docker-compose.yml` following the same pattern as other static sites (shock-strategy, spc-llc, upperlehman, datum24).

## Design
- **Light theme**: White/light-gray backgrounds, navy text, orange accents
- **Color palette** (CSS custom properties in `:root`):
  - `--navy: #0A2466` — primary brand color, headings
  - `--orange: #D4722A` — accent, CTAs, eyebrows
  - `--blue: #4A6FA5` — secondary accent
  - Light backgrounds: `#FFFFFF`, `#F2F4F7`
- **Hero**: Full-bleed background image (`homeANIM1-1920.jpg`) with navy gradient overlay
- **Footer/RFQ form**: Dark navy treatment for contrast
- **Logo**: `SequoiaPrecisionComponents - cropped.jpg` — dark text on white, inverted in footer via CSS filter

## Key Files
```
index.html                                  — Entire site (HTML + CSS + JS)
favicon.ico                                 — End mill icon favicon
SequoiaPrecisionComponents - cropped.jpg    — Primary logo (nav + footer)
Sequoia Automatic.gif                       — Legacy Sequoia Automatic logo
SAMill-removebg.png                         — End mill icon (transparent bg)
images/
  homeANIM1-1920.jpg                        — Hero background (CNC coolant)
  homeANIM2-1920.jpg                        — Factory/automotive split
  homeANIM3-1920.jpg                        — Brown & Sharpe CMM (quality banner)
  topWHY-1920.jpg                           — CNC drilling close-up (photo banner)
  topCAREERS-1920.jpg                       — CNC milling action
  SALG-1.jpg, SALG-2.jpg                   — Large heat sinks (gallery lead)
  SA BLACK.jpg                              — Black anodized heat sink
  GROUP OTHER.jpg                           — Mixed component group shot
  DIE CAST GROUP.jpg                        — Die cast machined parts
  SA FIVE HOLE.jpg                          — Multi-port valve body
  SA 2 THREADS UP.jpg                       — Threaded refrigerant connector
  SA MULTI DIM1/2.jpg                       — Multi-feature brackets
  DC-1.jpg, DC-3.jpg                        — Die cast housings
  DEN038.jpg, DEN041.jpg, DEN081.jpg, DEN106.jpg — Smaller machined parts
  DEW081-2.jpg, MMC783.jpg, SHO-011.jpg    — Small components
  SA B2-4.jpg, VCC001.jpg, VST026.jpg      — Connectors and fittings
  SA-logo-light.svg                         — Generated SVG logo (unused, replaced by JPG)
```

## Sections (in page order)
1. **Nav** — Fixed, white with blur backdrop
2. **Hero** — Full-viewport with background image, stats bar at bottom
3. **About** — Company story + timeline
4. **Photo Banner** — `topWHY-1920.jpg`
5. **Markets** — Automotive + Data Center thermal management cards
6. **Capabilities** — 6-card grid (CNC, Engineering, Quality, Volume, Materials, Intelligence)
7. **Product Gallery** — 6 product photos, heat sinks first
8. **Facilities** — 4 global locations (Crystal Lake, Saltillo, Nanjing, Chonburi)
9. **Quality Banner** — CMM photo with overlay text
10. **Quality** — Certifications and badges (IATF 16949, APQP/PPAP, SPC, Traceability)
11. **Contact** — Location cards + RFQ form
12. **Footer** — Dark navy, logo, nav links, legal

## Conventions
- All CSS uses custom properties from `:root`
- Scroll reveal via IntersectionObserver (`.reveal` → `.visible`)
- No external JS dependencies
- Images use `loading="lazy"` except hero
- Stat: **400+ CNC Machines** across all facilities
