# Project Retrospective, Google Step Up Career Challenge

**Project:** Gemini Pro Student Launch · Multi-Market Digital Marketing Campaign
**Submitted by:** Mulualem Kahssay
**Date:** May 2026
**Format:** Gibbs' Reflective Cycle (1988)

---

## 1. Description, *what happened*

I took on Digdata's Google Step Up Career Challenge, which asked entrants to plan a $10M, 8-week, 3-market digital marketing campaign for Gemini Pro targeting university students aged 18-24. The brief came with four datasets, 1,664 weekly rows of historic spend, 48 brand-lift studies, 240 creative tests, and a high-level results workbook, and two tracks to choose from: Path A (Data Science) or Path B (Data Strategist). I decided to do both, plus an interactive web app that turned the analysis into something a non-analyst could actually use.

The work landed as four deliverables:

- **`TaskA_Gemini_Pro_Insights.pptx`**, an 8-slide data-science deck walking through the methodology and the five insights the data produced.
- **`TaskB_Gemini_Pro_Strategy.pptx`**, a 9-slide strategist deck turning those insights into a defensible $10M plan: which markets, which channels, which creative, how to phase it, how to measure it.
- **`LiftIQ_GeminiPro_Console.html`**, a single-file interactive web app with six tabs covering markets, channels, brand-lift testing (including a live two-proportion z-test calculator), creative ranking, and a budget allocator with live forecast updates.
- **`Project_Retrospective.md`**, this document.

The headline finding was that MENA (Egypt and Saudi Arabia) converts students 3.8× more efficiently than the UK and Germany, that Display media has zero statistically-significant brand lift across 16 historic studies, and that one creative, "Life Hack", wins every market and every channel by a margin of more than 3×.

## 2. Feelings, *what I was thinking*

I felt confident going in because the GSK Step Up Challenge I'd just finished gave me a working pattern: ingest, test, visualise, recommend. But the Google brief was harder than it first looked. The historic CSV didn't have the campaign-name attribution column the questions assumed, that came from a separate workbook the brief casually mentioned. I burned an hour before noticing.

I also felt uncertain about whether to include Display in the recommendation. Display had the cheapest CPM ($4) and the largest reach (92M unique users), and dropping it on the basis of brand-lift insignificance felt aggressive. The relief came when I ran the z-tests and found 0/16 studies significant, the data was unambiguous, and that gave me the confidence to make the cut.

The most rewarding moment was watching the budget allocator in the web app respond live: drag the UK YouTube slider and the forecasted sign-ups update in real time using market-specific CPAs. That felt like the work had become a tool instead of a static document.

## 3. Evaluation, *what worked and what didn't*

**What worked:**

- **Two-proportion z-tests as the filter.** Treating "significance" as a hard gate and ignoring everything that didn't pass cut the brand-lift dataset from 48 studies to 32, and the 16 it dropped were almost entirely Display. The pattern that fell out of the data drove the most contrarian recommendation in the strategist deck.
- **Market × channel CPA heatmaps.** Looking at the data through that single lens revealed that Search converts cheaply *everywhere* ($3-12 CPA) while Display fails *everywhere* ($30-90 CPA). That made the "skip Display" call easier to defend.
- **Cross-deliverable consistency.** The same five insights appear in Task A, get translated into recommendations in Task B, and become explorable filters in the web app. The thread is visible.
- **Designing the web app last.** Building it after the analysis meant I knew exactly which interactions mattered. The z-test calculator, the budget slider, and the creative ranking were all decisions I had wished I could test interactively while writing the deck.

**What didn't:**

- **Spend column confusion.** I lost time before realising the canonical spend figures lived in `High_Level_Results.xlsx`, not the raw CSV. A first-pass schema check would have caught this in five minutes.
- **Slide layout iteration.** First render of Task A had three slides with overlapping text, big numbers spilling into their captions. I had to rebuild and re-screenshot. A cheap test grid (one slide with every text-size combination) would have caught this before I'd authored eight slides.
- **DE was a borderline call.** Germany's CPA is the same as the UK's ($23) but I dropped it and kept the UK. The strategic case (UK is brand HQ, closes the SOV gap) is real, but it's a values argument, not a data argument. I made it explicit in the deck rather than hiding it.

## 4. Analysis, *why it happened*

The technical wins traced back to a habit I formed on the GSK challenge: build a single canonical analysis script (`analyse.py`) that produces one clean JSON the deck and the web app both consume. That meant the number you see on slide 6 of Task A is provably the same number rendered in the Lift IQ Brand Lift tab, no risk of drift, no copy-paste errors. It also made iteration fast: when I tweaked the CPLU calculation, every downstream artefact updated.

The slide-layout problems traced back to authoring eight slides before rendering any. PptxGenJS positions text in inches with no auto-fit; a fontSize that looks right on paper can overflow its bounding box once converted by LibreOffice. The fix is to render after slide one and only continue once the type system is settled, a discipline I'll carry into the next project.

The DE call was harder because the brief's success criteria are mixed: efficiency *and* strategic value *and* SOV recovery. Pure efficiency would say drop UK and run EG/SA/IN. Pure strategy would say keep UK and DE. I navigated the trade-off by making the brand-HQ logic explicit on slide 3 of Task B, turning a soft argument into a stated assumption the reader can challenge.

## 5. Conclusion, *what I learned*

Three things I'm taking forward:

1. **Insignificance is a finding.** Display has been a default line item in digital marketing budgets for fifteen years. Looking at 16 brand-lift studies and finding zero passed p<0.05 was the most valuable thing the data said. Negative results, surfaced confidently, are a strategist's strongest tool.
2. **One canonical dataset, three surfaces.** Task A, Task B, and the web app all read from the same `app_data.json`. That separation between *what the data says* and *how I render it* is the difference between deliverables that can drift apart and ones that can't.
3. **Render early.** I should have screenshotted a single slide after writing slide one, not slide eight. Cheap tests prevent expensive rebuilds.

## 6. Action plan, *next time*

- **Schema audit first.** Before writing any analysis code, I'll dump `df.info()` and `df.head()` for every input file and sketch the join keys on paper. The lost hour on the spend column was avoidable.
- **Render-as-you-go for slide decks.** I'll add a `--slide=N` flag to the build script so I can render slide 1 alone before authoring the rest. This lets me tune the typography system once and inherit it everywhere.
- **Document trade-offs in line.** Where the data is genuinely ambiguous (the DE drop, the budget split between EG and SA), I'll keep noting the strategic assumption *on the same slide* as the recommendation. Reviewers should never have to guess which calls are data-led and which are values-led.
- **Build the interactive view before the deck.** The Lift IQ console clarified my thinking faster than the PowerPoint did. Next time I'll prototype the interactive surface first and let it shape what makes the cut for the deck.

---

*This retrospective was written immediately after submission, while the work was still warm. The Gibbs cycle is a teaching tool, but the intent here is honest, not academic. Where I made the wrong call, I've said so. Where I got lucky, I've said that too.*
