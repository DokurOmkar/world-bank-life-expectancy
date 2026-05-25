# World Bank Development Indicators: What Drives Life Expectancy?

A data science project following the **CRISP-DM** process to explore economic and health indicators for 217 countries (2000–2015) and build a predictive model for life expectancy.

---

## Motivation

Life expectancy is one of the most meaningful summary statistics for a country's development. By understanding which economic and social factors predict it — and to what degree — policymakers can prioritize where to invest. This project uses World Bank Databank data to answer five concrete questions about global development trends.

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
| Strongest correlates | Under-5 mortality rate (−0.89) and GNI per capita (+0.80) are the dominant predictors. Fertility rate (−0.82) and adolescent fertility (−0.78) also show strong negative correlations. |
| Regional GNI trends | Europe & Central Asia and North America led throughout. East Asia & Pacific showed the steepest growth. Sub-Saharan Africa remained lowest but grew modestly. |
| Child mortality champions | Rwanda led with a drop of 137 per 1,000 live births (74% reduction). Malawi, Angola, Liberia, and Niger followed — all in Sub-Saharan Africa. |
| Model accuracy | Gradient Boosting: Test R² = 0.912, MAE = 1.81 years — explains 91.2% of variance in life expectancy across 44 test countries. |
| Income scenario | Doubling GNI per capita alone adds only +0.4 predicted years. Moving to high-income levels ($40k GNI) adds ~10+ years — confirming that health investments matter far more than income alone. |

---

## Repository Structure

```
├── world_bank_analysis.ipynb   # Main analysis notebook (CRISP-DM)
├── world_bank_data.csv         # Raw World Bank Databank export (2000–2015)
├── README.md                   # This file
├── blog_post.md                # Non-technical blog post summary
├── fig_missingness.png         # Missingness heatmap for selected features
├── fig_correlations.png        # Feature correlations with life expectancy
├── fig_scatter_drivers.png     # GNI & child mortality scatter plots
├── fig_gni_regions.png         # GNI per capita time series by region (2000–2015)
├── fig_child_mortality.png     # Top 15 countries by child mortality improvement
├── fig_model_performance.png   # Predicted vs actual + residual plot
├── fig_feature_importance.png  # Gradient Boosting feature importances
└── fig_scenarios.png           # Life expectancy under income scenarios
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

## Key Model Results

| Model | CV R² | Test R² | MAE | RMSE |
|-------|-------|---------|-----|------|
| Ridge Regression | 0.845 ± 0.063 | 0.881 | 2.08 yrs | 2.85 yrs |
| Random Forest | 0.839 ± 0.044 | 0.906 | 1.93 yrs | 2.53 yrs |
| **Gradient Boosting** | **0.857 ± 0.034** | **0.912** | **1.81 yrs** | **2.44 yrs** |

**Note on metrics:** This is a regression task predicting a continuous variable (years). R², MAE, and RMSE are the regression equivalents of accuracy, recall, and F1 used in classification models.

- **R²** — fraction of variance explained (1.0 = perfect)
- **MAE** — average absolute error in years; model is typically within 1.81 years
- **RMSE** — penalizes large errors more heavily than MAE

---

## Blog Post

[What Determines How Long You'll Live? The Data Tells a Clear Story](https://github.com/DokurOmkar/world-bank-life-expectancy/blob/main/blog_post.md)

A non-technical summary of the findings written for a general audience.

---

## Data Source

World Bank Databank — **World Development Indicators**
Downloaded from: https://databank.worldbank.org
Coverage: 217 countries, 51 indicators, years 2000–2015
Last updated: February 2026

---

## Acknowledgements

- [World Bank Open Data](https://data.worldbank.org/) for freely available development indicators
- [Udacity Data Science Nanodegree](https://www.udacity.com/course/data-scientist-nanodegree--nd025) for project structure and guidance
- CRISP-DM methodology for the analysis framework
