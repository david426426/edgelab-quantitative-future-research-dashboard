# EdgeLab Methodology

EdgeLab describes historical regular trading hours (RTH) for E-mini S&P 500 futures (ES).

## Data and date ranges

- RTH runs from 09:30 to 16:00 Eastern Time (ET). Price and volume studies and cumulative Delta use complete RTH sessions. Other order flow reports use eligible observations with source records.
- Select any inclusive month range from January 2019 through August 2026. Presets and custom ranges use the same calendar-month summaries. The last complete session is August 28, 2026. The source ends on August 31, 2026 at 11:59 ET, during an incomplete session.
- Reports use unadjusted prices. Charts and tables are built from precomputed summaries.

## Rates and sample sizes

An event rate divides the event count by the number of eligible observations. For a multi-month range, the report pools the numerator and denominator before calculating the rate. For example, a first-break hold rate uses sessions with a clear first-break direction, and a positive Delta rate uses sessions with data in the relevant interval. The IB extension report can count all breakout episodes as separate observations.

Where applicable, the reports show 95% Wilson confidence intervals for session-level rates. Intervals are omitted for denominators below 30. When any weekday group in a month has fewer than three eligible sessions, the month contributes only to all-weekday totals. This rule affects March and June 2020 in this release.

## Price and volume reports

| Report | Calculation |
|---|---|
| Opening Range Breakout (ORB) | The opening range is the high and low during the selected interval. A breakout requires a subsequent one-minute high or low to strictly cross a boundary. Crossing both sides during a session counts as a double breakout. If both sides are crossed in the first breakout minute, direction is unclear. A close at a boundary counts as inside. First-break timing is grouped into 15-minute bins and extensions into 0.25× opening-range width steps. Retracement is measured after the first breakout bar on single-sided breakout days with positive range width. |
| Initial Balance (IB) | The selected opening window starts at 09:30 ET. Breakouts use the chosen bar interval and wick or close confirmation. The opposite-side break is measured from the next bar and can use a separate confirmation rule. Formation order uses the first appearance of each price extreme. |
| Gaps and opening behavior | The gap is the open relative to the previous eligible RTH close, with a minimum absolute size of one point. A gap fills when the selected level is reached by the close. Timing is grouped into 15-minute bins. Opening candle continuation uses directional opening candles, and opening location compares the open with the prior eligible session's high and low. |
| Range, volatility and Power Hour | ADR and ATR use prior eligible sessions, excluding the current session. Grouped range and extension percentiles are estimated from monthly distributions. Intraday range means use pooled interval totals and eligible sample counts. Power Hour compares 15:00–16:00 ET with the preceding RTH range. |

## Order flow reports

| Report | Calculation |
|---|---|
| Delta by Time of Day | Net Delta is aggressive buy volume minus aggressive sell volume, in contracts. The positive Delta rate uses sessions with data in each interval. |
| Cumulative Delta (CVD) | Daily change is the difference between the first and last valid RTH CVD readings. Price changes use the same endpoints. The curve accumulates the monthly sums of these daily changes. |
| Volume Profile | Contract volume is summed across eligible sessions in the selected months in 10-point price bins. The highest-volume bin is highlighted. |
| Large Trade Frequency | Counts large trade events flagged in the source. Eligible sessions with zero large trades remain in the denominator for the share of days with an event. Event count and contract volume are separate measures. |
| Buy/Sell Imbalance | Monthly volume-weighted imbalance divides net Delta by traded volume. Source records are grouped by positive, negative, or zero Delta. Source-record imbalance percentiles are calculated separately for each month. |

## Interpretation

The figures describe historical event frequency. Eligible samples can differ across reports and filters. Time and price bins limit the precision of reported estimates. The reports do not simulate fills, fees, slippage, or equity curves.
