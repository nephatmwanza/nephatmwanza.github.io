---
title: "Zambia's rain is changing shape, not amount"
date: 2026-07-27
summary: "Forty-five rainy seasons of satellite rainfall over Zambia. Rain now falls on more days and totals more, while the heaviest downpours weaken and the longest dry spell inside the season lengthens — a redistribution that seasonal totals hide entirely."
tags: ["climate extremes", "CHIRPS", "Zambia", "rainfall", "trend analysis", "Python"]
cover:
  image: "/img/fig2_trend_maps.png"
  alt: "Four maps of Zambia showing trend per decade in rainfall total, dry spell length, wet spell length and very-wet-day rainfall"
  caption: "Trend per decade in each index, 1981/82–2025/26. Blue is wetter, red is drier."
  relative: false
ShowToc: true
TocOpen: false
---

Ask whether Zambia is getting wetter or drier and you will get an argument. Forty-five
seasons of daily rainfall data give a more useful answer: **neither**. The rain is
redistributing.

| | |
|---|---|
| **Data** | CHIRPS v2.0 daily satellite–gauge rainfall, 0.25°, 1981–2026 |
| **Coverage** | 45 rainy seasons, 1981/82 – 2025/26 |
| **Headline** | 9 of 10 provinces show lengthening dry spells |
| **Code** | [github.com/nephatmwanza/zambia-rainfall-extremes](https://github.com/nephatmwanza/zambia-rainfall-extremes) |

---

## Why seasonal totals are the wrong thing to look at

Zambia has one rainy season, October to March. Nearly all the country's crop production
rides on it, and most of the population depends on that production directly.

Two things can go wrong inside a season that a rainfall total hides completely.

The first is a **dry spell**. Two or three weeks without rain in January, when maize is
tasselling, can fail a crop in a season whose total rainfall is entirely normal. The rain
arrived — just not when the plant needed it.

The second is a **cloudburst**: a single day heavy enough to flood, wash out roads and
destroy stored grain, in a season that ends up below average overall.

Both are invisible in a seasonal total. So instead of totals, I measured the *shape* of each
season — the longest unbroken dry spell, the longest wet spell, how much rain fell on the
wettest few days, and how many rain days there were at all. These are standard ETCCDI
indices, the same definitions the WMO's expert team on climate change detection uses,
computed for every 0.25° grid cell in Zambia across 45 seasons.

## What the data says

Three things move together, and the combination is the story.

{{< figure src="/img/fig2_trend_maps.png" alt="Four maps of Zambia showing trend per decade in seasonal rainfall total, longest dry spell, longest wet spell and very-wet-day rainfall" caption="How each measure of the rainy season has changed per decade since 1981. Blue means wetter, red means drier. Total rainfall is broadly rising, dry spells are lengthening across most of the country, and the heaviest downpours are weakening — three changes that only make sense together." >}}

**Rain is falling on more days.** Nine of Zambia's ten provinces show an increase in the
number of wet days, and nine of ten show an increase in total seasonal rainfall.

**But the heaviest downpours are getting weaker.** Nine of ten provinces show a *decline* in
how much rain falls on the most extreme days of the season.

**And the longest dry spell within the season is getting longer.** Again nine of ten
provinces — with the clearest signal in Southern Province, where the longest dry spell has
been lengthening by about **0.85 days per decade**, roughly four days across the record.

> Put those together and Zambia's rainfall is not so much increasing or decreasing as
> **redistributing**. More frequent, gentler rain; fewer violent downpours; and longer gaps
> in between.

{{< figure src="/img/fig5_province_cdd_smallmultiples.png" alt="Ten small line charts, one per Zambian province, showing the longest dry spell each season with a fitted trend line" caption="The longest dry spell in each rainy season, province by province, over 45 years. The jagged blue line is the year-to-year reality; the straight line is the underlying trend. Nine of the ten provinces trend upward — Eastern is the single exception." >}}

## Why this matters more than a wetter/drier headline

Southern Province is the sharpest illustration. It is already the driest part of Zambia —
685 mm a season against Luapula's 1,129 mm — and it is the country's recognised drought
hotspot. It is also where dry spells are lengthening fastest.

{{< figure src="/img/fig1_climatology.png" alt="Four maps showing average seasonal rainfall, dry spell length, wet spell length and very-wet-day rainfall across Zambia" caption="Average rainy-season conditions, 1981–2026. The north–south divide runs through everything: the wet north-east receives well over 1,000 mm a season, the dry south-west barely 700 mm. Southern Province sits at the dry end of that gradient." >}}

A planner working from seasonal totals would see nothing to worry about there. Total rainfall
is holding up. But the thing that actually fails a maize crop — a long dry gap in the middle
of the season — is the thing that is growing.

That is an argument for a different kind of response than "prepare for less rain":
drought-tolerant and shorter-cycle varieties, staggered planting, and small-scale water
storage that can bridge a three-week gap. It is a within-season problem, and it needs
within-season tools.

## The part where I say what this does *not* show

This is the point at which analyses like this usually overreach, so I want to be careful.

**Almost none of these trends is statistically significant on its own.** I tested each grid
cell and each province. After correcting for the fact that testing a thousand grid cells will
throw up dozens of false positives by chance, **not one cell survives**. The national
dry-spell trend has a p-value of 0.38 — nowhere near conventional significance.

{{< figure src="/img/fig4_national_series.png" alt="Four time series of Zambian national seasonal averages from 1981 to 2026, each with a fitted trend line, showing large year-to-year variability" caption="This is what \"not a long record\" looks like. Seasonal rainfall swings between under 700 mm and over 1,100 mm from one year to the next — while the trend line rises by about 6 mm per decade. The trend is real, but small compared to how much any single year can vary." >}}

Forty-five seasons is simply not very long when the year-to-year swings are as large as
Zambia's, which are driven substantially by El Niño and La Niña. Against that noise, a trend
of under a day per decade is very hard to prove.

So what am I claiming? Not that any single province has a proven trend. What is striking is
the **consistency of direction**. If nothing were happening, the ten provinces should split
roughly five and five on each index. Getting nine-to-one splits — and getting them on four
different indices that tell a physically coherent story — is much less likely to be an
accident than any individual province's result suggests.

{{< figure src="/img/fig3_province_trends.png" alt="Two horizontal bar charts ranking Zambian provinces by trend in longest dry spell and in very-wet-day rainfall" caption="Every province, ranked by how fast its dry spells are lengthening (left) and how its heaviest-rainfall days are changing (right). Colour shows direction only. Almost every bar points the same way on each chart — and that lopsidedness, rather than any single bar, is what the evidence rests on." >}}

I should flag the limit of even that argument: provinces sit next to each other and share the
same large-scale weather, so they are not ten independent observations. That makes the
coherence suggestive rather than conclusive.

> **"A coherent signal that has not yet cleared statistical significance"** is a genuinely
> different message from either "Zambia is drying" or "nothing is happening" — and for anyone
> making decisions on a ten-to-twenty-year horizon, it is the more actionable one.

## On getting it right

Two bugs in my own analysis are worth mentioning, because catching them changed the answer.

The standard correction for year-to-year correlation in this kind of test turns out to be
**anti-conservative** if applied naively — I checked it against pure random noise and found it
flagged nearly 10% of nonsense series as significant, against the 5% it should. Left alone, it
had inflated my results to 14 "significant" province trends. The correct number was 9.

Separately, a subtle tool behaviour — a routine for shifting dates in climate files — was
silently discarding one to two days from every single season, which would have quietly
corrupted every dry-spell length in the study.

Neither would have been visible in the output. Both were caught by writing checks that assert
what the answer *should* be on data where the answer is known: a calibration test on random
noise, and a day-count check against the calendar. Those checks now run every time the
analysis does.

---

## Method summary

| | |
|---|---|
| **Data** | CHIRPS v2.0 daily satellite–gauge rainfall, 0.25°, 1981–2026 |
| **Season** | ONDJFM, 1 October – 31 March, labelled by start year |
| **Baseline** | 1991/92–2020/21, the seasonal match to the WMO 1991–2020 normal |
| **Indices** | CDD, CWD, R95p, R99p (amount and day-count), PRCPTOT, R1mm — ETCCDI definitions |
| **Trend test** | Mann–Kendall with tie and serial-correlation corrections; Theil–Sen slope |
| **Multiple testing** | Benjamini–Hochberg false-discovery-rate control |
| **Tools** | CDO, Python (NumPy, SciPy, pandas, matplotlib), GeoPandas |

Everything is reproducible from public data. The repository contains the full pipeline, the
analysis notebook with all outputs, and the derived datasets.

[**View the repository →**](https://github.com/nephatmwanza/zambia-rainfall-extremes)
· [**The companion temperature study →**](/projects/zambia-temperature-extremes/)

> **A fair question about the result above:** if almost nothing is significant, was the test
> simply too weak? I answered it by running the identical pipeline on temperature over the
> same country and the same years — and finding **987 significant grid cells** against
> **zero** here. [See the temperature study →](/projects/zambia-temperature-extremes/)
