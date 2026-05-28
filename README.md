# Support & Resistance @ape_bitcoiner V1.0

Pine Script v6 indicator for TradingView. Auto-detects pivots, draws S/R lines, flags clean breakouts, retests with reversal bars, and shows higher-timeframe levels.

Based on the LuxAlgo v4 original, rewritten for Pine v6 with several additions.

**Files:**
- `support-resistance-breaks.pine` — English version.
- `support-resistance-breaks-ptbr.pine` — Versão em português (mesmo código, inputs e mensagens traduzidos).

## Features

- **Auto S/R lines** — pivots redrawn with `line.new`, old lines deleted when invalidated.
- **Break detection** — close-confirmed crossover/crossunder, filtered by volume and ATR.
- **ATR filter** — rejects weak breaks smaller than `atrMult × ATR` (default 0.25).
- **No repaint** — `confirmClose` toggle uses `barstate.isconfirmed`.
- **Bull/Bear Wick labels** — distinguishes clean breaks from rejection wicks.
- **Higher-timeframe S/R** — overlays daily/4h pivots on lower TFs via `request.security`.
- **Retest detection** — flags "RT" when price returns to a broken level **and** prints a reversal bar (hammer / engulfing).
- **Levels table** — top-left corner, shows active R/S, % distance, HTF levels, ATR.
- **Price tag on lines** — floating label at the right edge of each S/R line with its price (toggle via `Show Price Tag on S/R Lines`).
- **Alerts** — break and retest alerts with `{{ticker}}` / `{{interval}}` / `{{close}}` placeholders.

## Inputs

| Group | Key | Default | Notes |
|---|---|---|---|
| Pivots | Left / Right Bars | 15 / 15 | Wider = stronger pivots, fewer signals. |
| Breaks | Volume Threshold | 20% | Volume oscillator (EMA5 vs EMA10). |
| Breaks | Confirm on Close | true | Disable for intrabar alerts. |
| ATR | atrMult | 0.25 | Raise to 0.5–1.0 on the daily. |
| HTF | Higher Timeframe | D | Use 60/240 for scalping. |
| Retest | Max Bars | 20 | How long after a break to keep watching. |
| Retest | Touch Proximity | 0.5 × ATR | How close price must come to count as touch. |

## Install

1. Open TradingView → Pine Editor.
2. Paste the contents of `support-resistance-breaks.pine`.
3. Save → Add to chart.

## Tuning

- **BTC 15m / 1h:** `atrMult = 0.25`, volume filter on, HTF = D.
- **BTC daily:** `atrMult = 0.5–1.0`, HTF off.
- **Scalping low-volume sessions:** turn off `useVolFilter`.

## License

MIT.
