# Impact of Housing Supply on Rent Growth: A Difference-in-Differences Analysis

This project investigates whether U.S. metropolitan areas with higher levels of new housing construction experienced lower rent growth between 2015 and 2024, using a quasi-experimental Difference-in-Differences (DiD) design.

🔗 **[View the full analysis](https://yagoparada.github.io/housing-supply-rent-growth-did/)**

## 📋 Overview

Rising rents have consistently outpaced income growth in many U.S. cities over the past decade. This project tests whether increased housing supply — measured via building permits — is associated with slower rent growth, using:

- **H0**: Increasing housing construction does not affect rent growth in metropolitan areas.
- **Ha**: Increasing housing construction reduces rent growth in metropolitan areas.

## 🔬 Methodology

- Metropolitan areas were split into **Treatment** (high pre-pandemic construction) and **Control** (low construction) groups based on quintiles of pre-pandemic permit intensity, after filtering to the top 150 largest metros and removing population outliers via a standard deviation filter.
- Balance tables confirm comparability between groups on income, unemployment, and population.
- The study compares a **pre-treatment period (2015–2019)** to a **post-treatment period (2021–2024)**, excluding 2020 to isolate COVID-19 shock effects.
- Three model specifications were estimated: a basic DiD, a DiD with controls, and a **fixed-effects DiD model** (CBSA + Year fixed effects), the primary specification.
- Assumptions were validated using a Shapiro-Wilk normality test and Q-Q plot of residuals, with reliability supported by the Central Limit Theorem given the sample size (N = 452).

## 📊 Key Finding

The fixed-effects model found **no statistically significant treatment effect** (estimate = -0.0027, p = 0.517) over the full study period. However, the parallel trends plot reveals that both groups moved together during the 2020–2022 pandemic shock, with a divergence emerging in 2023–2024 where high-construction metros began showing lower rent growth — suggesting the effect may still be developing.

## 🗂️ Data Sources

- **Zillow Observed Rent Index (ZORI)** – monthly rent estimates by metro area
- **U.S. Census Bureau Building Permits Survey** – new housing units authorized
- **Census API / BLS** – population, median income, and unemployment rate (via `tidycensus`)

## 🛠️ Tools & Technologies

- **Language**: R
- **Data wrangling**: tidyverse, dplyr, purrr, readxl
- **Data acquisition**: tidycensus (Census API)
- **Statistical modeling**: fixest (fixed-effects regression), broom, modelsummary
- **Visualization**: ggplot2, DT (interactive tables)
- **Reporting**: Quarto (.qmd), published via GitHub Pages

## ✨ Features

- End-to-end reproducible workflow: multi-source data acquisition → cleaning/merging → quasi-experimental design → statistical inference
- Rigorous group comparability checks (balance tables, standard deviation filtering, quintile-based treatment assignment)
- Multiple model specifications compared side-by-side (basic DiD, controls, fixed effects)
- Assumption testing (Shapiro-Wilk, Q-Q plots) alongside the main analysis
