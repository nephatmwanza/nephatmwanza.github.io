---
title: "Most climate models can't reproduce a Zambian dry spell"
date: 2026-07-28
summary: "Before using a climate model to plan Zambia's future, it should be able to reproduce Zambia's present. Twenty-nine were tested against observations. Twenty-five rain on too many days — and that single error destroys exactly the thing that matters most to a farmer."
tags: ["climate extremes", "CMIP6", "Zambia", "model evaluation", "rainfall", "Python"]
cover:
  image: "/img/cmip1_drizzle.png"
  alt: "Scatter plot of 29 climate models by how often and how hard they rain, against the observed value"
  caption: "Each dot is a climate model. The star is reality. Almost all of them rain far too often."
  relative: false
ShowToc: true
TocOpen: false
---

My [rainfall study](/projects/zambia-rainfall-extremes/) found that the thing which actually
fails a Zambian maize crop is not a dry year. It is a **dry spell inside a wet season** — three
weeks without rain in January, in a year whose total rainfall looks perfectly normal.

Climate models are how anyone plans for the decades ahead. So the obvious next question is
whether they can be trusted with that particular quantity.

I tested twenty-nine of them. The answer is mostly no — and the reason is specific enough to
be useful.

| | |
|---|---|
| **Models tested** | 29 CMIP6 global climate models |
| **Benchmark** | CHIRPS satellite rainfall, 30 seasons, 1984/85–2013/14 |
| **Headline** | 25 of 29 rain on too many days |
| **Code** | [github.com/nephatmwanza/zambia-cmip6-evaluation](https://github.com/nephatmwanza/zambia-cmip6-evaluation) |

---

## The problem is not how much rain, it's how often

A model can produce roughly the right seasonal total by entirely the wrong route. So instead
of comparing totals, I split the rainfall into two separate questions: **how often does it
rain**, and **how hard when it does**.

{{< figure src="/img/cmip1_drizzle.png" alt="Scatter plot of 29 climate models showing wet-day frequency against wet-day intensity, with the observed value marked as a star" caption="Each dot is one model. The star is what actually happens in Zambia. Nearly every model sits to the right of it — raining on far more days than reality." >}}

In Zambia it rains on **55.6%** of rainy-season days. The typical model rains on **71%**. The
worst rains on **91%** — very nearly every single day of the season.

This is a known weakness of global climate models in the tropics: they drizzle. They produce
rain too often and too gently. What this study adds is what that costs you in Zambia
specifically.

## Why it destroys dry spells

Here is the thing that makes it matter rather than merely being untidy.

**A model that rains on 85% of days cannot produce a three-week dry spell.** There is no room
left in the calendar for one. The error in *frequency* forces an error in the exact quantity
that fails a crop.

If that's really the mechanism, then the models that rain too often should be the same models
that lose their dry spells. They are.

{{< figure src="/img/cmip2_mechanism.png" alt="Scatter plot showing that models raining on more days have shorter dry spells, with a strong negative correlation" caption="Every extra wet day comes out of a dry spell. The relationship is strong and consistent across the ensemble." >}}

Statistically, how often a model rains explains **63%** of how wrong its dry spells are. How
*hard* it rains explains **2%**. So this is one error with one cause, not a general vagueness.

The worst cases are severe. Two models produce a longest dry spell of around **seven days**
where the real figure is **nineteen** — barely a third of reality, in the measure that
determines whether a harvest survives.

## Averaging the models hides all of this

{{< figure src="/img/cmip3_dryspell.png" alt="Bar chart of dry spell length for each of the 29 models against the observed value" caption="Each bar is one model's dry spell against the observed 18.8 days. Red bars are more than four days out." >}}

A common shortcut is to average all the models together and treat that as the best estimate.
Here, the average dry spell across the ensemble is **17.1 days** against **18.8** observed —
which looks like excellent agreement.

It is an illusion. The individual models range from **7 to 34 days**, and only **6 of 29** are
within two days of reality. The average looks right only because large errors in opposite
directions cancel each other out. Averaging wrong answers does not produce a right one.

## So which models can you actually use?

{{< figure src="/img/cmip4_skill.png" alt="Scatter plot of overall model skill score against dry-spell error, coloured by wet-day frequency" caption="Overall skill on the horizontal axis, dry-spell error on the vertical. Good on one is not good on the other." >}}

**Not simply the ones at the top of the ranking.** Three findings make that clear:

- The model that gets dry spells closest to reality ranks only **10th** overall.
- The model with the best spatial pattern of all twenty-nine still overestimates dry spells by
  **eleven days**.
- One model lands within a day of the observed dry spell while ranking **26th of 29**, with
  almost no spatial skill. That is coincidence, not competence — and it is exactly the trap of
  picking a model on a single number.

The defensible choices are the models that do well on **both** counts:

| Model | Overall rank | Dry-spell error |
|---|---|---|
| **HadGEM3-GC31-MM** | 1st | −1.9 days |
| **HadGEM3-GC3-1-LL** | 4th | −1.1 days |
| **UKESM1-0-LL** | 10th | −0.4 days |

And several should simply not be used for agricultural or dry-spell work in Zambia without
correction first — those raining on more than 83% of days.

{{< figure src="/img/cmip5_spatial.png" alt="Maps of rainfall bias for the three best and three worst models" caption="Rainfall bias against observations: the three best-scoring models on top, the three worst below." >}}

## What this is for

This is not an argument against climate models. It is an argument for **checking them against
the thing you actually care about** before you rely on them.

For anyone in Zambia doing agricultural planning, seasonal forecasting or downscaling, the
practical conclusions are:

1. **Do not use the raw ensemble for dry-spell work.** Most of it drizzles, and the error runs
   in a consistent direction.
2. **Do not average and stop.** The mean conceals a spread from seven to thirty-four days.
3. **Select models against your own variable**, and check that a good score on it is not
   accidental.
4. **Weight the observational record heavily** for near-term planning. What has actually
   happened is better documented than what the models say happened.

That last point is where this connects back. The [rainfall study](/projects/zambia-rainfall-extremes/)
found dry spells lengthening across nine of ten provinces. This one says most climate models
are poorly equipped to carry that particular signal forward — which makes the observed record
more valuable, not less.

---

**Data:** 29 CMIP6 models, historical experiment, daily precipitation, conservatively
regridded onto the CHIRPS grid. Benchmark: CHIRPS v2.0 over the 30 shared October–March
seasons.
**Methods:** ETCCDI-style rainfall indices separating frequency from intensity; area-weighted
comparison; composite skill score across four indices plus spatial pattern correlation.

[**Code and full results on GitHub →**](https://github.com/nephatmwanza/zambia-cmip6-evaluation)
· [**The rainfall study →**](/projects/zambia-rainfall-extremes/)
· [**The temperature study →**](/projects/zambia-temperature-extremes/)
