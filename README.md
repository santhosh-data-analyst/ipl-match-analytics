# IPL Match Analytics

End-to-end exploratory data analysis on 17 years of IPL data — 1,095 matches and 260,920 deliveries — answering five specific business questions using Python, pandas, matplotlib, and seaborn.

📓 **[View full analysis on Kaggle](https://www.kaggle.com/code/santhoshreddykallam/ipl-data-analysis-project)**

---

## Business Problem

IPL teams, broadcasters, and fantasy platforms make high-stakes decisions — squad selection, commentary strategy, player valuation — with limited structured analytical backing. This project answers five concrete business questions from the data.

---

## Five Business Questions & Findings

**Q1. Who is the most economical death-over bowler in IPL history?**
> **M Theekshana** — economy rate of **6.73** in overs 17–20 (qualifier: minimum 60 balls bowled in death overs). The T20 death-over average is typically above 10 runs/over, making 6.73 exceptional.

**Q2. Who is the most reliable death-over batter?**
> **AB de Villiers** — strike rate of **223.78** from **635 balls** faced in overs 17–20. The qualifier threshold ensures only established death-over specialists are ranked, not small-sample outliers.

**Q3. Do chasing teams win more than teams batting first?**
> **Yes — 578 chasing wins vs 498 batting-first wins** across 1,076 matches with a decided result. That is a 54% vs 46% split in favour of chasing teams across IPL 2008–2024.

**Q4. Which grounds produce the closest finishes?**
> **Wankhede Stadium (Mumbai)** and **Eden Gardens (Kolkata)** produce the highest number of close finishes, consistent across seasons.

**Q5. Do batters perform differently in league matches vs knockout matches?**
> **Yes — league match batters record higher strike rates than knockout batters**, suggesting match pressure reduces scoring aggression in the knockout stage.

---

## Dataset

| File | Rows | Columns | Description |
|---|---|---|---|
| `matches.csv` | 1,095 | 20 | One row per match — teams, venue, toss, winner, margin |
| `deliveries.csv` | 260,920 | 17 | One row per delivery — bowler, batter, runs, dismissal |

- **Source:** [Kaggle — IPL Complete Dataset by Prateek Bhardwaj (2008–2024)](https://www.kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020)
- **Average deliveries per match:** ~238 (higher than 120 due to extras — wides and no-balls are re-bowled and appear as separate rows)

---

## Tools Used

| Tool | Version | Purpose |
|---|---|---|
| Python | 3.x | Core language |
| pandas | — | Data loading, cleaning, transformation, aggregation |
| matplotlib | — | Custom visualizations |
| seaborn | — | Statistical plots |

---

## Key Technical Steps

**Data Cleaning**
- Standardised team names across seasons (e.g., Delhi Daredevils → Delhi Capitals, Kings XI Punjab → Punjab Kings)
- Handled NULLs in `city`, `player_of_match`, and dismissal columns (expected for non-wicket deliveries)
- Excluded wides from balls-faced counts for strike rate calculations

**Feature Engineering**
- Death overs are defined as `over >= 16` (0-indexed) — overs 17–20
- Economy rate: `(total_runs / legal_balls) * 6`
- Strike rate: `(batsman_runs / balls_faced) * 100`, excluding wides
- Close finish: matches decided by ≤ 5 runs or ≤ 1 wicket (last ball)

**Qualifier Thresholds**
- Bowler ranking: minimum 60 deliveries bowled in death overs
- Batter ranking: minimum 100 balls faced in death overs
- These thresholds prevent small-sample outliers from dominating the rankings

---

## Limitations

- Data ends at IPL 2024 — 2025 season, not included
- No pitch type, weather, or ball-speed data — venue comparisons are based on match outcomes only
- Findings Q3 and Q5 are descriptive (EDA), not inferential — a chi-square or t-test would be required to confirm statistical significance
- Kaggle dataset — validated structurally, not independently verified against BCCI official records

---



*Published as part of portfolio — B.E. CSE, Sathyabama University | [LinkedIn](https://www.linkedin.com/in/santhosh-reddy-kallam) | [GitHub](https://github.com/santhosh-data-analyst)*
