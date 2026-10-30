# Does Money Buy Wins in La Liga?

An Excel analysis of how closely club wage bills predict league points in La Liga, and which clubs consistently get more (or less) than their wages suggest.

The analysis covers **five seasons (2019–20 through 2023–24)** and **100 club-season observations**.


## Key Results

- **Wages are strongly tied to points.** Across 100 club-seasons, the correlation between wage index and league points is **0.79**, with an **R² of 0.63**. This means about 63% of the variation in league points is associated with variation in the wage index in this linear model.
- **Real Sociedad was the strongest consistent overperformer**, finishing approximately **13.9 points per season above expectations** across all five seasons despite having a below-average wage bill.
- **Real Betis (+9.1)** and **Atlético Madrid (+9.0)** also consistently outperformed expectations.
- **Espanyol (-10.9)** and **Elche (-9.3)** were among the largest underperformers, although both only appeared in three of the five seasons.
- **Real Madrid and Barcelona** finished roughly 4 points below the linear trendline despite their very large wage bills. One possible explanation is that league points have a natural ceiling, causing a linear model to overestimate expected points at very high wage levels. This is a hypothesis rather than a proven cause.

## The Question

**Does a bigger wage bill buy more points, and which clubs get the most (or least) out of their money?**

## Data

- **Source:** Standings and squad wage tables from [FBref](https://fbref.com) (Sports Reference)
- Wage estimates on FBref come from [Capology](https://www.capology.com)
- **Coverage:** La Liga, 2019–20 through 2023–24
- **Sample:** 20 clubs per season and 100 club-season observations

> **Note:** Many wage figures are partly or fully estimated, particularly for smaller clubs. The `% Estimated` column in the workbook indicates how much of each figure is estimated.

Standings and wage data courtesy of [Sports Reference (FBref)](https://fbref.com) and [Capology](https://www.capology.com).

## Method

1. Copied each season's wage table and standings table from FBref into Excel and preserved an untouched raw copy.
2. Cleaned wage text into numerical euro values using `VALUE`, `MID`, and `FIND`.
3. Joined each club's league points to its wages using `XLOOKUP` and corrected club-name mismatches such as accents and spelling differences.
4. Calculated **cost per point** using annual wages divided by league points.
5. Combined all five seasons into one `all_seasons` table.
6. Created a **wage index** by dividing each club's wages by the average wage bill for that season (1.0 = average wages that season), allowing different seasons to be compared more fairly.
7. Measured the relationship between wages and points using `CORREL` and `RSQ`.
8. Calculated expected points using `FORECAST.LINEAR`, based on the linear relationship between wage index and league points.
9. Calculated **points vs. expected** as actual points minus expected points.
10. Summarized club performance using a pivot table and retained clubs with at least three seasons of data.

## Workbook Guide

The analysis is contained in `laliga_wages_vs._points.xlsx`.

**How to use it:** Open the workbook in Excel and start with the `findings` sheet. Some formulas, including `XLOOKUP` and `FORECAST.LINEAR`, require Excel 2021 or Microsoft 365.

| Sheet | Purpose |
|---|---|
| `findings` | Summary of key statistics, top and bottom clubs, findings, recommendations, and limitations |
| `charts_all_seasons` | Scatter plot of wage index vs. league points with a trendline |
| `pivot_clubs` | Average points vs. expected, average wage index, and seasons by club |
| `all_seasons` | Combined 100-row dataset and analysis formulas |
| `wages_*` | Wage data and working sheets for individual seasons |
| `standings_*` | League standings for individual seasons |
| `charts_*` | Season-specific charts |
| `raw_wages_*` | Original FBref wage data retained as a backup |

## Findings in More Detail

### Top Overperformers

| Club | Avg. Points vs. Expected | Wage Index | Seasons |
|---|---:|---:|---:|
| Real Sociedad | +13.9 | 0.68 | 5 |
| Real Betis | +9.1 | 0.62 | 5 |
| Atlético Madrid | +9.0 | 2.41 | 5 |

### Bottom Underperformers

| Club | Avg. Points vs. Expected | Wage Index | Seasons |
|---|---:|---:|---:|
| Espanyol | -10.9 | 0.42 | 3 |
| Elche | -9.3 | 0.24 | 3 |
| Valladolid | -6.3 | 0.27 | 3 |
| Alavés | -5.7 | 0.29 | 4 |
| Cádiz | -4.7 | 0.29 | 4 |
| Granada | -4.3 | 0.33 | 4 |

Results for clubs with only three seasons should be interpreted with greater caution because of the smaller sample.

## Recommendation

Wage spending explains much of the variation in league performance, but clubs such as **Real Sociedad and Real Betis** demonstrate that spending is not destiny.

A club considering whether to increase its wage bill could first investigate what consistent overperformers do differently, including areas such as recruitment and squad stability.

This analysis identifies the **pattern**, but it does not establish what causes certain clubs to outperform their wage levels.

## Limitations

- Wage figures from FBref via Capology are partly or fully estimated, especially for smaller clubs.
- Five seasons is a relatively small sample.
- Promoted and relegated clubs appear in fewer seasons.
- Clubs with fewer than three seasons were excluded from the club-level comparison.
- A straight-line trendline is a simple model and may not fully capture the relationship at very high wage levels.
- The analysis demonstrates **association, not causation**.
- Wage figures were not adjusted for inflation or squad size.

## Tools & Excel Skills

**Microsoft Excel**

- `XLOOKUP`
- `AVERAGEIFS`
- `CORREL`
- `RSQ`
- `FORECAST.LINEAR`
- `VALUE`
- `MID`
- `FIND`
- Pivot tables
- Scatter charts
- Trendlines
- Data cleaning and transformation

## Next Steps

Potential extensions of this project:

- Recreate the analysis using **SQL**
- Run a regression using **Python** and compare it with the Excel trendline
- Test whether a nonlinear model better explains performance among the highest-spending clubs
- Extend the analysis to other European leagues

## About

Built by **Abel (Abilmansur) Zinaddin**, a Business Data Analytics student at Arizona State University.

[LinkedIn](https://www.linkedin.com/in/abel-zinaddin)
