# Food Delivery Data — Cleaning & KPI Analysis

A data cleaning and analysis project on a food-delivery order dataset, built with **Python (pandas)** and **Power BI**. The project takes a raw, messy dataset through a full cleaning pipeline and produces business KPIs and a manager-facing dashboard.

> **Note:** This is a practice project built on a synthetic (sample) dataset created to demonstrate cleaning and analysis workflows.

## Project Overview

The goal was to turn ~14,700 raw order records into trustworthy data and a clear set of business KPIs — the kind of workflow a BI or operations analyst runs on monthly data.

## Tools Used

- **Python (pandas)** — data cleaning and KPI calculation
- **Power BI (DAX)** — interactive dashboard and measures

## Data Cleaning (Python)

The raw dataset contained the six most common data-quality problems. Each was diagnosed before being fixed:

- **Missing values** — filled numeric gaps with the median, text gaps with `"Unknown"`
- **Duplicates** — removed 1,115 duplicate rows (only detectable *after* standardizing text and types)
- **Impossible values** — negative and zero delivery times, plus a `999` sentinel value, converted to blanks then handled
- **Inconsistent text** — standardized casing, whitespace, and abbreviations (e.g. `Sthlm` → `Stockholm`)
- **Wrong data types** — converted currency text (`"248 kr"`, `"270,0"`) to numbers, and mixed-format text dates to proper datetimes

Result: a clean dataset of ~13,600 reliable records.

## Key KPIs

- **Total revenue:** 3,408,647 SEK
- **Average delivery time:** 37.8 minutes
- **On-time delivery rate:** ~83% (17% late)
- **Top cities by revenue:** Stockholm, Göteborg, Uppsala
- **Top cuisines by revenue:** Pizza, Burgers, Sushi
- **Returning-customer share** and per-category breakdowns

## Power BI Dashboard

An interactive dashboard presents the KPIs with cards, charts, and slicers for filtering by city, cuisine, and customer type. Measures were built in DAX (`SUM`, `AVERAGE`, `COUNTROWS`, `CALCULATE`, `DIVIDE`).

## Files

- `Food_data.ipynb` — Python cleaning and KPI notebook
- `Food_Data_messy.csv` — the raw dataset
- `Food_orders_clean.csv` — the cleaned output
- `dashboard.pbix` — Power BI dashboard

## Key Takeaways

- Data must be standardized (text + types) *before* duplicates can be reliably detected.
- Cleaning decisions (median vs mean, "Unknown" vs blank) should be deliberate and explainable.
- The workflow is structured to be repeatable on next month's data.
