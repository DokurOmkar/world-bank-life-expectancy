# World Bank Development Indicators: What Drives Life Expectancy?

A data science project following the **CRISP-DM** process to explore economic and health indicators for 217 countries (2000–2015) and build a predictive model for life expectancy.

---

## Motivation

Life expectancy is one of the most meaningful summary statistics for a country's development. By understanding which economic and social factors predict it and to what degree policymakers can prioritize where to invest. This project uses the World Bank Databank data to answer five concrete questions about global development trends.

---

## Questions of Interest

1. **Which World Bank indicators correlate most strongly with life expectancy?**
2. **How has GNI per capita evolved across world regions from 2000 to 2015?**
3. **Which countries made the biggest gains in reducing under-5 child mortality?**
4. **Can we build a reliable model to predict a country's life expectancy from its indicators?**
5. **What does the model predict for a hypothetical "median developing country" under different income scenarios?**

---

## Summary of Results

| Question | Key Finding |
|----------|-------------|
| Strongest correlates | Under-5 mortality rate (−0.93) and GNI per capita (+0.83) dominate |
| Regional GNI trends | East Asia & Pacific showed the steepest income growth; Sub-Saharan Africa the lowest but growing |
| Child mortality heroes | Ethiopia, Niger, Mali, Chad led absolute drops in under-5 deaths over 2000–2015 |
| Model accuracy | Gradient Boosting: Test R² = 0.912, MAE = 1.81 years — explains 91% of variance |
| Income scenario | Doubling GNI per capita in a median LMIC adds ~2–4 predicted life years; reaching high-income levels adds 10+ |

---

## Repository Structure

```
├── world_bank_analysis.ipynb   # Main analysis notebook (CRISP-DM)
├── world_bank_data.csv         # Raw World Bank Databank export (2000–2015)
├── README.md                   # This file
├── fig_missingness.png         # Missingness heatmap
├── fig_correlations.png        # Feature–target correlations
├── fig_scatter_drivers.png     # GNI & mortality scatter plots
├── fig_gni_regions.png         # GNI per capita time series by region
├── fig_child_mortality.png     # Top 15 child mortality improvements
├── fig_model_performance.png   # Predicted vs actual + residuals
├── fig_feature_importance.png  # Gradient Boosting feature importances
└── fig_scenarios.png           # Income scenario predictions
```

---

## Libraries Used

| Library | Version | Purpose |
|---------|---------|---------|
| `pandas` | ≥1.3 | Data loading, reshaping, analysis |
| `numpy` | ≥1.21 | Numerical operations, log transforms |
| `scikit-learn` | ≥1.0 | Imputation, scaling, models, evaluation |
| `matplotlib` | ≥3.4 | Base plotting |
| `seaborn` | ≥0.11 | Statistical visualization |

Install all dependencies:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

---

## How to Run

```bash
# Clone / download the repository, then:
jupyter notebook world_bank_analysis.ipynb
# Run all cells top-to-bottom (Kernel → Restart & Run All)
```

---

## Data Source

World Bank Databank — **World Development Indicators**  
Downloaded from: https://databank.worldbank.org  
Coverage: 217 countries, 51 indicators, years 2000–2015  
Last updated: February 2026

---

## Acknowledgements

- [World Bank Open Data](https://data.worldbank.org/) for providing freely available development indicators
- [Udacity Data Science Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025) for project structure guidance
- CRISP-DM methodology for the analysis framework
