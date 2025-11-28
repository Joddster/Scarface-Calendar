# Day Trading Performance Calendar

A visual dashboard that tracks daily trading performance, aggregating results by day, symbol, and timeframe (weekly / monthly / yearly / all-time). The app is built with Vite + React so it runs locally with `npm run dev` and can be deployed to Vercel without any backend work.

## Features

- Month-style calendar that highlights winning vs losing days with trade counts and net P&L per tile.
- Sidebar filter to focus on a single symbol or view all stocks at once.
- Modal editor for any day so you can log P&L and number of trades with instant calendar updates.
- Win/loss calculation cards with quick toggles for weekly, monthly, yearly, and all-time views.
- JSON importer that can seed multiple years of history (existing entries get updated instead of duplicated).
- LocalStorage persistence for edits plus a starter seed in `src/data/seedData.js`.

## Getting Started

```bash
npm install
npm run dev
```

Open http://localhost:5173 to view the dashboard during development.

### Build & Deploy

```
npm run build
```

The build output in `dist/` can be deployed directly to Vercel. Keep the default Vite build command (`npm run build`) and output directory (`dist`).

## Importing Historical Data

1. Prepare a JSON array where each element looks like:

```json
{
  "date": "2024-09-18",
  "stock": "AAPL",
  "pnl": 1200,
  "trades": 3
}
```

2. Click **“Import JSON history”** in the sidebar and select your file. Existing days (matched by `date + stock`) will be overwritten; new days are appended.
3. You can also edit `src/data/seedData.js` if you prefer to bundle a static set of records.

## Notes

- All state is kept client-side; no authentication or backend services are required.
- Styling lives in `src/App.css` for quick tweaking, and utility helpers are under `src/utils/tradingUtils.js`.
