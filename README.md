# Sequoia Precision Components — Website

Marketing website for Sequoia Precision Components — global precision CNC machining for automotive and data center thermal management.

## Quick Start

Serve locally with any static file server:

```bash
# Docker (Nginx)
docker run -d --name sequoia-website -p 8081:80 \
  -v $(pwd):/usr/share/nginx/html:ro \
  nginx:alpine

# Python
python3 -m http.server 8081

# Node
npx serve -p 8081
```

Then open [http://localhost:8081](http://localhost:8081).

## Stack

- Single `index.html` — no build step, no framework
- Inline CSS + vanilla JS
- Google Fonts (DM Sans, JetBrains Mono)
- Responsive (mobile, tablet, desktop)

## Structure

```
index.html          — Full site (HTML + CSS + JS)
favicon.ico         — Browser tab icon
images/             — Product photos, hero/banner images
*.jpg / *.gif / *.png — Logo assets
CLAUDE.md           — AI assistant context file
```
