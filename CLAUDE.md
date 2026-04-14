# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Environment

- **Python:** Use the `scraping` conda environment for all Python work.
  ```bash
  conda activate scraping
  jupyter notebook scraping_bonheur_education.ipynb
  ```
- **R:** The dashboard requires the following packages: `flexdashboard`, `tidyverse`, `plotly`, `DT`, `corrplot`, `scales`.
  ```r
  rmarkdown::render("dashboard.Rmd")
  ```

## Project Overview

Academic data science project (IMT Mines Alès – 2IA) exploring the link between education level and happiness across countries. The central research question: *Does a country's education level predict its population's happiness?*

**Data sources:** Wikipedia (scraping) and World Bank (API/download).

## Architecture

| File | Role |
|------|------|
| `scraping_bonheur_education.ipynb` | Python notebook — scrapes Wikipedia and World Bank data, cleans and merges it, exports `happiness_education_dataset.csv` |
| `happiness_education_dataset.csv` | Combined dataset (~190 countries, 15 variables) — the bridge between the notebook and the dashboard |
| `dashboard.Rmd` | R Markdown flexdashboard — 4 tabs: Introduction (world map + KPIs), Design of Experiment, Analyse exploratoire, Analyse prédictive |
| `dashboard.html` | Pre-rendered static output of `dashboard.Rmd` |
| `rapport_trame.docx` | Report template (Word) |

## Key dataset columns

`country`, `education_index` (HDI component), `happiness_score`, `rank_happiness`, `gdp_per_capita_log`, `social_support`, `healthy_life_exp`, `freedom_choices`, `generosity`, `corruption_perception`, `literacy_rate_pct`, `gov_expenditure_edu_pct_gdp`, `school_enrollment_secondary_pct`, `school_enrollment_tertiary_pct`, `tertiary_attainment_pct`

## Python dependencies (conda `scraping`)

`requests`, `requests-ratelimiter`, `beautifulsoup4`, `pandas`, `numpy`, `geopandas`, `jupyter`
