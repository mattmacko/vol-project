# Does it matter how you measure realized volatility?

Volatility forecasts are scored against "realized volatility," but that isn't
something you observe, it's something you estimate, and there are several
reasonable ways to do it. If reasonable people compute it differently, does the
winning forecast model change?

Using three years of Intel tick data (~25M trades), I build three estimates of
each day's variance and ask that question twice: once about the estimate used to
**grade** forecasts, and once about the estimate used to **train** them.

## What I found

**Grading barely matters.** Hold two forecasts fixed and switch the answer key,
and the measured gap between them moves by three parts in a thousand
(−0.0770 vs −0.0774). Model rankings are unchanged under all three estimates.

**Training matters enormously for some models.** A persistence forecast built
from squared daily returns scores +96.7. The identical model built from intraday
realized variance scores −5.35, graded against the same target. A fitted model
works out how much to trust a noisy input and discounts it automatically while
a rule that says "tomorrow equals today" trusts its input completely.

Measurement error in what you're judged against averages out. Measurement error
in what you act on doesn't, because you act before you know it was error.

## Start here

**[`notebooks/04_results.ipynb`](notebooks/04_results.ipynb)** — the full writeup,
with every figure and table.

## Everything else

| | |
|---|---|
| `01_signature.ipynb` | Picking the sampling interval (30s) from tick data |
| `02_proxies.ipynb` | Building the three daily variance estimates |
| `03_forecast.ipynb` | Naive, GARCH(1,1), and HAR forecasts; QLIKE scoring |
| `04_results.ipynb` | **Results and discussion** |

Data: INTC trades, Databento XNAS.ITCH, Jan 2023 – Dec 2025.
Not redistributed — `01` and `02` need your own pull; `03` and `04` run from the
cached daily panel in `data/`.