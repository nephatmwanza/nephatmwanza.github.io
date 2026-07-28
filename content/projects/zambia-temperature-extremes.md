---
title: "Heat is rising where rainfall is not"
date: 2026-07-28
summary: "The same test, run on temperature instead of rainfall over the same country and the same 45 years, gives the opposite answer. The hottest day of the year is rising in all ten Zambian provinces — and that is what makes the rainfall result believable."
tags: ["climate extremes", "ERA5", "Zambia", "temperature", "trend analysis", "ENSO", "Python"]
cover:
  image: "/img/heat2_trend_maps.png"
  alt: "Four maps of Zambia showing the trend per decade in mean daily maximum temperature, hottest day, warm days and days above 35 degrees"
  caption: "Trend per decade, 1981–2025. Red is warming. Stippling marks statistical significance."
  relative: false
ShowToc: true
TocOpen: false
---

My [rainfall analysis](/projects/zambia-rainfall-extremes/) ended on an honest but
unsatisfying note: Zambia's rainy season is *reorganising*, but not one grid cell showed a
trend strong enough to survive proper statistical scrutiny.

That raises a fair question. **Was the test simply too weak?**

So I ran it again — same country, same 45 years, same baseline, same code — and changed only
one thing: temperature instead of rainfall.

The answer came back completely different.

## What the data says

{{< figure src="/img/heat2_trend_maps.png" alt="Four maps of Zambia showing trend per decade in mean daily maximum temperature, hottest day of the year, days above the 90th percentile, and days above 35 degrees Celsius" caption="Trend per decade, 1981–2025. Red is warming, blue is cooling. The dark stippling marks cells where the trend is statistically significant — compare how much of the map is stippled here against the equivalent rainfall map." >}}

**The hottest day of the year is getting hotter by 0.35 °C every decade.** Across 45 years,
that is about **1.6 °C** added to Zambia's annual peak.

**Days above 35 °C are increasing by two per decade.** In the 1980s Zambia averaged about
five such days a year. It now averages thirteen.

Both trends are statistically significant in **every single one of the ten provinces**. Not
most. All ten.

| Measure | Change per decade | Provinces where it is significant |
|---|---|---|
| Hottest day of the year | **+0.35 °C** | **10 of 10** |
| Days above 35 °C | **+2.1 days** | **10 of 10** |
| Average daily maximum | +0.11 °C | 4 of 10 |

{{< figure src="/img/heat3_national_series.png" alt="Two time series from 1981 to 2025 showing the hottest day of the year and the number of days above 35 degrees, both rising" caption="The two measures with a robust trend. Unlike anything in the rainfall data, the upward slope here is large compared with the year-to-year scatter." >}}

## Why this makes the rainfall result more believable, not less

This is the part I find most useful, and it is the reason the two studies belong side by side.

A negative result is always vulnerable to the same objection: *maybe your method just could
not detect anything.* The only convincing answer is to show the method finding something
elsewhere — using the same code, on the same place, over the same years.

After correcting for the fact that testing a thousand grid cells throws up false positives by
chance:

| | Grid cells with a trend that survives correction |
|---|---|
| Hottest day of the year | **987** of about 1,009 |
| Days above 35 °C | **720** |
| **Every rainfall measure** | **0** |

The pipeline detects trends perfectly well when they are there. Zambia's rainfall genuinely
does not have a detectable one over this record. Its temperature emphatically does.

That is also what physics predicts. Warming shows up in the temperature record faster than
changes in circulation show up in rainfall, because rainfall is noisier and its drivers are
more complicated. It is more satisfying to demonstrate that on one country's data than to
cite it.

## Where the heat is

{{< figure src="/img/heat1_climatology.png" alt="Four maps showing average temperature conditions across Zambia" caption="Average conditions, 1981–2025. Temperature follows elevation rather than the north–south pattern that governs rainfall." >}}

Zambia's heat map is not its rainfall map. Temperature follows **elevation**.

**Northern Province**, up on the high plateau, averages just **0.2 days above 35 °C** a year.
**Eastern Province**, which contains the low-lying Luangwa Valley, averages **22**. Western
and Southern, also low, sit close behind.

{{< figure src="/img/heat5_province_trends.png" alt="Two bar charts ranking Zambian provinces by warming rate in hottest day and days above 35 degrees" caption="Every province is warming on both measures, and every one significantly." >}}

## The two measures that show no trend — and why that is a finding

Two of the five indices show no significant trend at all. That is not a failure of the
analysis; it is a real property of Zambian temperature.

{{< figure src="/img/heat4_enso.png" alt="Two time series with El Nino years highlighted in red, showing that the peaks coincide with El Nino events" caption="The warmest years, marked in red, are El Niño years." >}}

**Nine of the ten warmest years on record coincide with an El Niño event.** The two
percentile-based measures track each other almost exactly, and both spike in the same
years — 1983, 1987, 1992, 1998, 2005, 2016, 2019, 2023, 2024.

One of them, the warm-spell measure, is extreme in this respect. Most years it sits near
zero. In a strong El Niño it can exceed 60 days. Against swings of that size, a robust
statistical method correctly refuses to claim a steady trend — even though the *average*
across decades is clearly rising.

Reporting "no trend" here is the honest answer, and the El Niño structure is itself the
result. It also tells a planner something practical: Zambia's worst heat years are, to a
useful degree, **forecastable months ahead**, because ENSO is forecastable.

## What the two studies say together

They point at two different kinds of planning problem.

**For rainfall, plan for variability rather than for a direction.** The record does not
support a confident claim that Zambia is getting wetter or drier. It does support a
redistribution — rain on more days, in gentler falls, with longer gaps between.

**For heat, plan for a trend.** It is unambiguous, present in every province, and largest in
exactly the measure that matters for stress on crops and people: the extreme end, not the
average.

**And the two compound.** Inside the growing season, the hottest day is rising by 0.36 °C per
decade and days above 35 °C by 1.6 per decade — the same window in which dry spells are
lengthening. Higher temperatures raise the water a crop needs at precisely the moment a
longer dry spell would deny it. Neither study shows that alone. The pair does.

---

**Data:** ERA5 daily maximum temperature, 0.25°, 1981–2025. Baseline 1991–2020.
**Methods:** ETCCDI temperature indices with a calendar-day 90th percentile on a 5-day
window; Mann–Kendall with tie and serial-correlation corrections; Theil–Sen slope;
Benjamini–Hochberg false-discovery-rate control.

[**Code and full results on GitHub →**](https://github.com/nephatmwanza/zambia-temperature-extremes)
· [**The companion rainfall study →**](/projects/zambia-rainfall-extremes/)
