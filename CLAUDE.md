# Intel Analyzer

Single-file sports betting analytics dashboard (`index.html`). Hosted via GitHub Pages at https://pluribuspoker.github.io/intel-sheets-tracker/

## Architecture

- Everything lives in one HTML file — HTML structure, CSS (Tailwind CDN + custom styles), and vanilla JS
- No build step, no framework, no backend
- CSV parsing via PapaParse, charts via Chart.js, styling via Tailwind CDN
- Dynamic column detection: the app scans CSV headers to find pick/odds/units/profit/league/date columns automatically

## Key Concepts

- **Units (u)** — Standard betting unit size. Profit/loss measured in units
- **ROI** — Return on investment: `profit / units_wagered * 100`
- **Momentum** — Streak-based analysis: performance following N consecutive wins/losses
- **Position** — Favorite vs Dog (underdog), derived from spread if not explicitly in CSV

## Working With This Codebase

- Open the HTML file directly in a browser to test — no server needed
- All state is in JS variables (`allPicksData`, `activeFilters`, `cachedFilteredData`, etc.)
- The main data pipeline: CSV → `processWithDynamicStart()` → `updateDashboard()` → renders all panels
- Filters modify `activeFilters`/`numericFilters` → `updateDashboard()` re-filters and re-renders
