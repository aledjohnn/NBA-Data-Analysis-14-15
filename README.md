# NBA 2014–15 Season: Exploratory Data Analysis

**Authors:** Aled John & Roman Galaky, Cardiff University — MA2502  
**Language:** R (Jupyter Notebook, IR kernel)  
**Dataset:** [NBA Shot Logs 2014–15](https://www.kaggle.com/datasets/dansbecker/nba-shot-logs) — 124,343 shot attempts across 903 games

---

## What This Project Does

This notebook investigates three questions about the 2014–15 NBA season using shot-level data:

1. **Who are the best two-way players?** — Building a composite Impact Score that balances offensive efficiency (Points Per Shot) against defensive presence (opponent FG% during estimated on-court windows)
2. **Does rest time affect win probability?** — Testing whether the number of days between games predicts match outcomes using chi-squared and Monte Carlo permutation tests
3. **Does altitude give Denver and Utah a measurable home edge?** — Comparing home/away shooting splits at high-altitude venues against the rest of the league

---

## Key Findings

**Two-way impact**
- Top performers by Impact Score are dominated by efficient rim-protecting big men (centers) Deandre Jordan, Tyson Chandler, Rudy Gobert. These players score at high percentages and suppress opponent shooting during their time on court
- A Welch t-test (p = 0.367) finds no statistically significant difference in two-way impact between high-usage "stars" and role players, consistent with the offensive burden hypothesis: stars take harder, more contested shots that naturally reduce efficiency metrics

**Rest days vs. win rate**
- Win rates across 1-day, 2-day, 3-day, and 4+ day rest groups all sit within 95% confidence intervals that overlap 0.5, no rest group shows a statistically significant edge
- Chi-squared test: χ² = 2.26, p = 0.52. Confirmed by a Monte Carlo permutation test (p = 0.40) using a custom Linear Congruential Generator built from scratch rather than R's built-in `sample()`

**Altitude home advantage**
- Denver Nuggets (Ball Arena, 5,280 ft) and Utah Jazz (Delta Center, 4,226 ft) play at two of the highest venues in professional sport
- Home/away FG% gaps are compared between altitude games and the rest of the league, with a specific focus on three-point accuracy, the shot type most sensitive to air resistance and ball arc
- A two-proportion z-test tests whether home teams at altitude shoot significantly better than home teams elsewhere, and whether visiting teams shoot meaningfully worse at altitude venues than at sea level

---

## Methods and Tools

| Category | Detail |
|---|---|
| Language | R 3.6.1 |
| Environment | Jupyter Notebook (IR kernel) |
| Statistical tests | Welch t-test, Pearson chi-squared, two-proportion z-test, binomial proportion CI |
| Simulation | Monte Carlo permutation test (10,000 permutations) |
| Custom implementation | Linear Congruential Generator (LCG) built from scratch using Borland C++ constants |
| Visualisation | Base R graphics — scatter plots, bar charts, boxplots, histograms with error bars |
| Data wrangling | `aggregate()`, `merge()`, `tapply()`, `factor()` |

---

## Project Structure

```
NBA-Data-Analysis-14-15/
├── README.md
├── README.tex
├── SETUP.md
├── nba_data_analysis.ipynb     ← main analysis notebook
├── data/
│   ├── Shot_data_clean.csv     ← place Kaggle data here (see setup below)
│   └── Players_clean.csv
└── output/
    └── group_report.pdf        ← full group findings report (7 authors)
```

---

## How to Run

**1. Clone the repo**
```bash
git clone https://github.com/aled-john/NBA-Data-Analysis-14-15.git
cd NBA-Data-Analysis-14-15
```

**2. Get the data**  
Download the NBA Shot Logs dataset from Kaggle:  
[kaggle.com/datasets/dansbecker/nba-shot-logs](https://www.kaggle.com/datasets/dansbecker/nba-shot-logs)

Place `Shot_data_clean.csv` and `Players_clean.csv` into the `data/` folder.

**3. Install the IR kernel (if needed)**
```bash
install.packages('IRkernel')
IRkernel::installspec()
```

**4. Open and run**
```bash
jupyter notebook nba_data_analysis.ipynb
```
Run all cells top to bottom, the notebook is fully sequential.

---

## Authorship Note

This notebook was produced as part of a 7 person group project for MA2502 at Cardiff University. **Aled John and Roman Galaky** are responsible for the analyses in this notebook specifically, the two-way impact model (Section 1), the rest days analysis (Section 2), and the altitude home advantage extension (Section 3).

The full group report covering all five analytical questions is included in `output/group_report.pdf`.

