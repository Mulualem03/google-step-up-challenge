# Google Step Up Career Challenge: Gemini Pro Student Launch

A response to Digdata's Google Step Up Career Challenge: plan a $10M, 8-week, 3-market digital marketing campaign to drive Gemini Pro consideration and sign-ups among university students aged 18-24.

Submitted across both routes, **Path A (Data Science)** and **Path B (Data Strategist)**, plus an interactive web app and a project retrospective.

---

## Deliverables

| File | Route | What it is |
|---|---|---|
| `TaskA_Gemini_Pro_Insights.pptx` | Path A | 8-slide data-science deck. Methodology and five insights from 1,664 weekly rows, 48 brand-lift studies, 240 creative tests |
| `TaskB_Gemini_Pro_Strategy.pptx` | Path B | 9-slide strategist deck. Markets, channels, $10M allocation, creative, 8-week phasing, KPIs |
| `LiftIQ_GeminiPro_Console.html` | Companion | Single-file interactive console with 6 tabs, live z-test calculator, and a budget allocator with real-time forecast |
| `Project_Retrospective.md` | Reflection | Gibbs' reflective cycle (6 stages) on what worked, what didn't, and what I'd do next time |

---

## The five insights (Path A)

1. **MENA converts 3.8x more efficiently than UK/DE.** Egypt $6.33 CPA, Saudi Arabia $6.16 CPA, vs UK $23.70 and Germany $23.25.
2. **Display is dead weight.** 0/16 brand-lift studies passed p<0.05. CPM is cheapest at $4 but CPA is $57, which is 10x Search.
3. **YouTube and Social are the only channels that move consideration.** Average CPLU $0.35 to $0.37, with around 70% relative lift.
4. **EG and SA on YouTube/Social move students for under $0.30 each.** All top-8 lowest-CPLU campaigns sit in MENA.
5. **"Life Hack" wins every market and every channel.** +10.1pp consideration lift among 18-24s, which is 3.3x the next-best creative.

## The four decisions (Path B)

1. **Markets:** UK, Egypt, Saudi Arabia. Drop Germany.
2. **Channels:** YouTube, Social, Search. No Display.
3. **Budget:** $10M split 35/35/30 across markets, 40/30/30 across channels.
4. **Creative:** Life Hack as hero (70%). Coding Help (20%) and Study With Me (10%) as supports.

Forecast: ~1.18M Gemini Pro sign-ups, +8pp consideration lift, 30%+ UK SOV by Sept 15.

---

## Methodology

* **Two-proportion z-tests** on every brand-lift study. Only p<0.05 results made the cut (32 of 48).
* **Cost Per Lifted User (CPLU)** computed as `spend / (reach * absolute lift)`. This is the efficiency metric the strategist deck rests on.
* **Single canonical analysis** in `analyse.py` (not committed, see deck for outputs) feeds one JSON consumed by both decks and the web app, so numbers can't drift.

---

## Stack

* **Analysis:** Python, pandas, statsmodels
* **Decks:** PptxGenJS (programmatic, version-controlled slides)
* **Web app:** vanilla HTML/CSS/JS, single file, no dependencies
* **Design:** Google-adjacent palette (#1A73E8 / #EA4335 / #FBBC04 / #34A853), Fraunces, Inter Tight, JetBrains Mono

---

## About

Submitted by **Mulualem Kahssay**, May 2026.
Path A: Data Science. Path B: Data Strategist.
