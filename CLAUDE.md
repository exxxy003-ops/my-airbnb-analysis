# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static site for "Hospitality in Era of Airbnb" — a MUSA-620 final project analyzing New York City Airbnb data. It is built on the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) Jekyll theme and published at https://liziqun.github.io/MUSA620_Final_Project/.

The project has two distinct parts:
1. **Jekyll website** (`_posts/`, `_layouts/`, `_includes/`, `_sass/`, `assets/`, `charts/`) — the published blog/site
2. **Python analysis** (`Data & Code/MUSA620_final project code.ipynb`) — the Jupyter notebook where charts and images were originally generated

## Commands

```bash
# Serve locally (requires Ruby/Bundler)
bundle exec jekyll serve

# Build static site into _site/
bundle exec jekyll build

# Rebuild minified JS bundle after editing assets/js/_main.js or plugins
npm run build:js

# Watch JS for changes
npm run watch:js
```

## Architecture

### Chart Embedding System

Posts embed interactive charts using three custom Jekyll includes, each with a corresponding front matter key:

- **Altair/Vega-Lite** (`altair-loader`): renders JSON specs from `charts/*.json` via `vegaEmbed` in the browser. Front matter maps a div ID to a JSON file path.
- **Folium** (`folium-loader`): injects Folium-generated HTML files from `charts/folium_*.html` into iframes. Front matter maps a div ID to `[path, height_px]`.
- **HvPlot** (`hv-loader`): injects hvPlot-generated HTML files from `charts/hvplot_*.html` into auto-resizing iframes. Front matter maps a div ID to a path.

Example front matter:
```yaml
folium-loader:
  folium-chart-1: ["charts/folium_overview.html", "400"]
altair-loader:
  altair-chart-1: charts/altair_price_distribution.json
hv-loader:
  hv-chart-1: "charts/importance_bar.html"
```

In the post body, use a `<div id="..."></div>` with the matching ID to place each chart.

### Post Structure

Posts in `_posts/` follow the naming convention `YYYY-MM-DD-N.Title.md` and are numbered 1–5:
1. Background/introduction
2. Exploratory analysis (Folium maps, Seaborn static images)
3. Neighbourhood analysis for guests (Altair, Folium, HvPlot)
4. Top-earned Airbnb for hosts (Altair, HvPlot)
5. Pricing tip prediction via Random Forest model

Static images (PNG) live in `assets/images/` and are referenced via raw GitHub URLs in posts. Generated chart files (HTML/JSON) live in `charts/`.

### Theme Customization

- `_config.yml` controls global site settings, author profile, and per-post defaults
- `_sass/minimal-mistakes/` contains the theme's SCSS partials; `assets/css/main.scss` imports them
- `_layouts/` and `_includes/` extend/override Minimal Mistakes defaults
- The compiled JS bundle is at `assets/js/main.min.js`; source is `assets/js/_main.js` + `assets/js/plugins/`
