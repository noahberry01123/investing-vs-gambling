# S&P 500 — 20-Year Return Explorer

An interactive widget for exploring how the S&P 500 performed over any 20-year
holding period from 1928 to today — in nominal **and** inflation-adjusted dollars,
with or without dividends reinvested.

Pick a start year, flip a couple of toggles, and watch a $10,000 investment grow
(or not) across the following two decades.

**▶ [Open the interactive tool](https://noahberry01123.github.io/SNP500-20-Year-Return-Widget/)**

> _The live link is served via GitHub Pages from `index.html` at the repo root. You can
> also download `index.html` from this repo and open it directly in any browser — no
> server needed._

## What you can do

- **Choose any start year** (1928–2025) with a slider or by typing it in, and see
  the next 20 years play out.
- **Switch between nominal and real returns** — toggle inflation-adjusted (CPI-U)
  dollars on or off to see how much purchasing power actually survived.
- **Reinvest dividends** — toggle a constant 3%/yr reinvested dividend yield to
  compare price-only growth against an approximate total return.
- **Read the headline numbers** — cumulative return, annualized return (CAGR), and
  what $10,000 turns into over the window.
- **See the path, not just the endpoint** — a chart rebases the index to 100 at the
  start year and compounds each year's return, so you can watch the drawdowns and
  recoveries along the way.

Start years after 2006 don't yet have a full 20 years of data; the widget detects
this and shows the partial window with a clear note instead of a misleading number.

## What you'll discover

Over the S&P 500's full history, a 20-year buy-and-hold has been remarkably
reliable — but **not foolproof**, and the answer hinges on whether you measure in
nominal or inflation-adjusted dollars (and whether you count dividends).

Across the 79 complete 20-year windows (start years 1928–2006), **price return only**:

- **Nominal:** only **3** windows ended below where they started — those beginning
  in **1928, 1929, and 1930**, swallowed by the Great Crash and Depression. Every
  start year from 1931 on finished positive.
- **Real (inflation-adjusted):** **17** windows lost purchasing power, in two
  clusters — the **Great Depression** (1928–1931) and the **1960s–70s stagflation
  era** (1955, 1956, and 1959–1969). The worst was the **1929** start: **−55.7%** in
  real terms over 20 years.
- **Add 3% reinvested dividends** and the picture transforms: **zero** negative
  nominal windows, and only **two** that still lost real purchasing power — start
  years **1929 (−20.0%)** and **1962 (−1.3%)**.

The takeaway the widget is built to make tangible: dividends and time horizon do
most of the heavy lifting, and "the market always goes up over 20 years" is mostly —
but not entirely — true.

## Data & method

- **Index:** S&P 500 (`^GSPC`) year-end closing prices via Yahoo Finance, 1927–2025.
  Data begins at year-end 1927, so the first full calendar-year return is 1928.
- **Returns:** annual **price returns** = year-over-year change in the year-end close.
  Dividends are excluded unless the dividends toggle is on.
- **Inflation:** real returns deflate by U.S. CPI-U (BLS series `CUUR0000SA0`,
  December values) — the same consumer price index the Federal Reserve publishes
  seasonally adjusted as `CPIAUCSL`. CPI-U extends back to 1913, so inflation-adjusted
  figures are available across the entire 1928–2025 range.
- **Dividends:** the toggle applies a constant **3% annual yield, reinvested** (each
  year's growth is multiplied by 1.03, compounding to ~1.81× over 20 years). This is a
  simplification — the index's actual trailing yield was often 4–6% for much of the
  20th century and below 2% in recent years — so it understates dividends for early
  windows and slightly overstates them for recent ones.
- **Window:** a start year *S* means buying at the start of year *S* and holding 20
  years, through the end of *S*+19. Cumulative return compounds the annual returns;
  annualized return is the compound annual growth rate (CAGR).

## How it's built

A **single, self-contained HTML file** (`index.html`, ~15 KB). The return and
inflation series are baked in as JavaScript constants, so the widget makes **no API
calls** and stores no data — its only external dependency is
[Chart.js](https://www.chartjs.org/) (4.4.4), loaded from a CDN to draw the graph.
No build step, no framework, no tracking. The layout is responsive (max-width 760px)
and works on mobile.

## License

Released under the **GNU General Public License v3.0** — see [`LICENSE`](LICENSE).
