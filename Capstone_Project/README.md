# Auditing the EPL Market: Can Expected Goals Beat the Bookmakers?

**Author:** Angel Diaz-Nova  
**Course:** DATA 205 (Capstone)  
**Date:** December 17, 2025

---

## Project Overview
The English Premier League (EPL) betting market is one of the most efficient financial markets in the world. This project conducts an operational audit of market efficiency by testing whether a predictive model based on Expected Goals (xG)—a metric of "Process"—can identify pricing inefficiencies in bookmaker odds, which are often driven by "Results."

**Hypothesis:** The market overreacts to short-term variance (luck). A model based on rolling xG should be able to identify mispriced assets (value bets).

## Repository Structure
* **`data/`**: Contains raw datasets.
  * `EPL FBref.csv`: Match stats and xG metrics (Source: FBref/Opta).
  * `EPL Odds.csv`: Historical closing odds (Source: Football-Data.co.uk).
* **`scripts/`**: R code for data cleaning, EDA, and modeling.
  * `EPL_Audit_Main.Rmd`: The master R Markdown file containing the full analysis pipeline.
* **`docs/`**: Final deliverables.
  * `Final_Report.docx`: The comprehensive written audit.
  * `Final_Presentation.pptx`: The slides used for the oral defense.

## Methodology (The Pipeline)
1.  **Harmonization:** Merged disparate datasets using a custom key-mapping algorithm (solving 'Man Utd' vs 'Manchester United' conflicts).
2.  **Feature Engineering:** Calculated **10-game Rolling Averages** for xG Created/Conceded.
3.  **Lag Control:** Applied a **1-Match Lag** to ensure zero data leakage (predicting Match N using only N-10 to N-1).
4.  **Validation:** Implemented **Walk-Forward Validation** (Training on 2017-2020 -> Predicting 2021) to simulate real-world trading constraints.

## Key Results
* **Total Matches Ingested:** 2,869
* **Walk-Forward Test Sample:** 1,480 Matches
* **Total Bets Placed:** 501
* **Win Rate:** 34% (Indicates model identified value in underdogs)
* **Strategy ROI:** -7.29%
* **Conclusion:** The xG variable was statistically significant (p < 2e-16), confirming it predicts match outcomes. However, the negative ROI confirms the **Strong-Form Efficient Market Hypothesis**; the bookmaker's margin (vig) eroded the model's theoretical edge.

##️ Tools Used
* **Language:** R (4.2+)
* **Libraries:** `tidyverse`, `zoo`, `lubridate`, `scales`, `ggrepel`, `pROC`

---
*For questions, please get in touch with Angel Diaz-Nova.*