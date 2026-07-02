# tradetest — Kalshi paper-trading tracker

Live dashboard tracking a longshot-NO maker strategy against the real Kalshi
order book. **No orders are placed** — phantom resting orders are filled only
when real buyer volume clears the queue ahead of them, to measure whether the
edge is actually executable before any real money is deployed.

- **Dashboard:** https://josh-max2.github.io/tradetest/
- `index.html` — the dashboard (fetches `data/paper.json`, auto-refreshes every 60s).
- `data/paper.json` — exported from a local SQLite DB by `publish_dashboard.py`,
  committed here every few minutes.

The measurement engine (`paper_tracker.py`, `publish_dashboard.py`) runs locally
and pushes data updates to this repo. Decision gate at day 14: fill-conditional
EV ≥ +1¢ and adverse-fill rate ≤ 5%.
