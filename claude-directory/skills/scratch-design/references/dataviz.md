# Data visualization

Read before building a chart, a dashboard, or any screen that shows numbers.

## Start from the question

- Write the reader's question in one line: "Which day sells the most passes?",
  "Is churn getting better?". The chart answers that question and nothing else.
- Know the reader: someone glancing at a dashboard needs the answer; an analyst
  needs to explore. Design for one.
- The title states the answer ("Saturdays sell twice as many passes as any
  other day"). The subtitle says what is measured, the unit, where and when.
  A source line goes underneath.

## Choose the form

| Question | Form | Notes |
|---|---|---|
| Compare categories | Bar chart, sorted | Horizontal when labels are long. Bars start at zero. |
| Change over time | Line chart | 4 to 5 lines at most; otherwise small multiples, or one line highlighted against gray. The y-axis need not start at zero, but say so if the change looks dramatic. |
| A few values over time | Column chart | When periods are discrete (months, quarters) and there are under about 12. |
| Rank and change in rank | Slope chart or dot plot | Two points in time: slope chart. |
| Part of a whole | Stacked bar or 100 % bar | A pie or donut only for two or three parts, with labels on the slices. |
| Distribution | Histogram, strip plot, box plot | Show the points when there are few enough. |
| Relationship | Scatter plot | Add a trend line only if it's meaningful. Label the outliers that matter. |
| Many series at once | Small multiples | Same scales across panels, so they compare. |
| Place | Choropleth for rates, dots or proportional symbols for counts | Big empty areas shouldn't dominate. |
| One number | The number, its change and a comparison | "1,284 passes · +12 % on last month" with a small sparkline. |
| Exact lookup | A table | Sometimes the table is the best chart. |

Avoid: 3D anything, dual y-axes, gauges and speedometers, radar charts for
comparison, word clouds, and stacked areas with many layers.

## Encoding

- People judge position best, then length, then angle and slope, then area, then
  color. Put the comparison that matters on position.
- Bars encode length, so their baseline is zero. Never truncate a bar axis.
- Don't double-encode without reason (bar length and color for the same value).
- Order means something: sort by value unless the categories have a natural
  order (days, sizes, age bands).

## Color

- Gray for context, one color for the point. Highlighting is the most useful
  thing color does in a chart.
- Categorical: 6 to 8 colors at most, distinct in lightness as well as hue, safe
  for color-blind readers (the Okabe-Ito set is a good start). If you need more,
  you need a different chart.
- Sequential: one hue, light to dark, for ordered values. Darker means more.
- Diverging: two hues around a neutral midpoint, and the midpoint is meaningful
  (zero, a target, an average).
- Never red against green as the only difference. Check the chart in grayscale.
- Chart marks need at least 3:1 contrast against the background, and text at
  least 4.5:1.
- Keep colors stable: the same series is the same color on every chart.

## Labels and annotation

- Label directly: names at the ends of lines, values on or beside bars. A legend
  is a last resort, and then it follows the data's order.
- Few ticks, round numbers, units in the axis label or the first tick ("$0",
  "10k").
- Gridlines faint or gone. Remove borders, backgrounds and anything else that
  isn't data.
- Annotate the moment that matters ("New pricing, March 3") with a short line
  and a few words, placed so it doesn't cover data.
- Numbers: tabular figures, consistent decimals, thousands separators,
  abbreviations (1.2M) with the full value in a tooltip.
- Dates: a format that can't be misread ("Mar 3" or "2026-03-03"), never
  "03/04".

## Dashboards

- Lead with the one or two numbers people come for, top left. Then trends, then
  detail.
- 5 to 7 tiles per view. More means two dashboards, or a filter.
- One time range for the whole view, shown clearly and easy to change.
- Every number has a comparison (last period, target, average), or it has no
  meaning.
- Align charts on a grid with shared axes where they compare. Keep tiles' type
  and color identical.
- Empty, loading and error states for every tile. "No data for this range" is
  different from zero.

## Interaction

- Tooltips show exact values and the label, and follow the pointer without
  covering the point.
- Hover is never required: tap and keyboard focus show the same information.
- Filters and highlights update the chart with a short transition (300 to
  500 ms) that keeps object constancy: the same bar moves; it doesn't vanish
  and reappear.
- On phones, make charts taller than wide, switch long category labels to
  horizontal bars, use fewer ticks, and never rotate labels.

## Accessible charts

- A text summary that states the takeaway, near the chart.
- The data as a real table, visible or one click away.
- SVG charts: `role="img"` and an `aria-label` with the takeaway, or a labelled
  `figure` with a `figcaption`.
- Keyboard focus can move between data points where interaction matters.
- Patterns or direct labels so color isn't the only cue.

## Chart checklist

1. Does the title state the answer?
2. Is the form the simplest one that answers the question?
3. Do bars start at zero, and is the sort order meaningful?
4. Is every series labeled without a trip to the legend?
5. Is color doing one job, and does the chart work in grayscale?
6. Are units, time range and source stated?
7. Is there a text summary and a table of the data?
