# Investing vs Gambling — Interactive Tools

Two small, self-contained web tools about **expected value** and the **law of large
numbers** — the ideas at the heart of the difference between investing and gambling.
They accompany the article *“The Difference Between Investing and Gambling Is One Number.”*

**▶ [Open the tools](https://noahberry01123.github.io/investing-vs-gambling-tools/)**

The landing page links to both tools, and every page has a tab bar at the top so you can
switch between them. Each tool is a single HTML file with no dependencies except a
CDN-hosted copy of Chart.js, so you can also download any file from this repo and open it
directly in a browser — no server needed.

---

## The tools

### 🫙 The Marble Jar — `marble_jar_widget.html`
A probability sandbox. Build a jar of winning (green, **+$1**) and losing (red, **−$1**)
marbles, then:

- **Pull marbles by hand** and watch a small number of draws stay noisy and unpredictable.
- **Run the long game** (up to 10,000 draws) and watch your running result — in dollars —
  converge toward the jar's expected value.
- Toggle the chart between **cumulative dollars** and **average per draw** to see your path
  squeeze toward the dashed expected-value line as the number of draws grows.
- Configure the jar however you like (marble counts and payouts) to flip between a
  positive-EV "investing-like" jar and a negative-EV "gambling-like" one.

### 📈 S&P 500 — 20-Year Return Explorer — `sp500_widget.html`
Pick any start year from 1928 onward and see how the S&P 500 performed over the following
20 years:

- **Nominal or inflation-adjusted** (real) returns, via U.S. CPI-U.
- **With or without dividends** reinvested (a simplifying 3%/yr assumption).
- Cumulative return, annualized return, a line chart of a $10,000 investment, and a clear
  note when a full 20-year window runs past the available data.

---

## Data & method (S&P 500 tool)

- **Prices:** S&P 500 (`^GSPC`) year-end closes via Yahoo Finance, baked into the page as
  annual returns (no live data calls).
- **Inflation:** U.S. CPI-U (BLS series `CUUR0000SA0`, December values) — the index FRED
  publishes seasonally adjusted as `CPIAUCSL`. CPIAUCSL begins in 1947; the underlying
  CPI-U extends back to 1913, so real returns are available across the whole 1928–2025 range.
- Returns are **price returns** (the dividend toggle adds an assumed flat 3%/yr). They are an
  illustration, not investment advice.

The marble tool's outcomes are simulated live with the browser's random-number generator,
so every run differs — that's the point.

---

## Deploying / hosting

The site is served by **GitHub Pages** from `index.html` at the repo root on the `main`
branch. To embed a tool elsewhere (e.g. a Medium article), link to its page on the Pages
site — the tools are full, standalone pages.

## License

See [LICENSE](LICENSE).
