# Pandas Notes

A structured collection of hands-on notebooks documenting my journey learning **pandas** for data analysis and data cleaning — built as part of my path toward becoming an AI/ML Engineer, and as a practical foundation for data cleaning work.

Each notebook focuses on a core pandas skill area, with explanations, reasoning, and working examples rather than just code snippets. The goal is not just to show *what* was done, but *why* — the reasoning behind each decision, especially around data cleaning, is documented alongside the code.

## Notebooks

| Notebook | Topics Covered |
|----------|----------------|
| [`Creating_&_Loading_Data.ipynb`](Creating_%26_Loading_Data.ipynb) | Creating DataFrames from scratch, loading data from CSV/other sources, initial data inspection |
| [`Selecting_&_Filtering_Data.ipynb`](Selecting_%26_Filtering_Data.ipynb) | Indexing, boolean filtering, `.loc`/`.iloc`, conditional selection |
| [`Modifying_Data_&_Creating_New_Column.ipynb`](Modifying_Data_%26_Creating_New_Column.ipynb) | Editing existing data, creating derived/calculated columns, feature engineering basics |
| [`Sorting_&_Ranking.ipynb`](Sorting_%26_Ranking.ipynb) | Sorting by single/multiple columns, ranking methods |
| [`Data_Cleaning.ipynb`](Data_Cleaning.ipynb) | End-to-end cleaning of a realistic messy e-commerce dataset — missing values, inconsistent formatting, outliers, duplicates, and type conversions (see details below) |
| [`Grouping_and_Aggregation.ipynb`](Grouping_and_Aggregation.ipynb) | `groupby()`, aggregation functions, `transform()` for group-based imputation |

## Featured: Data Cleaning Case Study

`Data_Cleaning.ipynb` is the most in-depth notebook in this repo. It works through a **messy, intentionally realistic e-commerce orders dataset** (~660 rows) and documents a complete cleaning pipeline, including:

- **Missing data strategy** — comparing `dropna()` vs. targeted filling, with reasoning for why each column was handled differently (median/mode/context-based imputation vs. `"Unknown"` placeholders)
- **Type correction** — converting text-like numeric columns (`age`, `unit_price`, `quantity`) to proper numeric types using `pd.to_numeric(errors='coerce')`
- **Format standardization** — cleaning inconsistent casing, currency symbols, and multi-word variants (e.g. `PKR`, `Rs.`, `$` prefixes; `EasyPaisa` vs `Easy Paisa`)
- **Outlier detection** — identifying and handling impossible values (e.g. age of `999`, quantity of `100`) using domain reasoning and cross-column checks
- **Group-based imputation** — filling missing prices using the median price *per product* rather than a single blanket value, for more realistic estimates
- **Duplicate resolution** — distinguishing between exact duplicate rows and *conflicting* duplicates (same `order_id`, differing field values), and resolving conflicts using logical rules (e.g. preferring final order statuses over `Pending`)

Every cleaning decision is documented in markdown/comments explaining the reasoning, not just the mechanics — intended to reflect how cleaning would be approached on a real client dataset.

## Data

The `data/` folder contains the datasets used across these notebooks:

- **Iris dataset** — classic dataset used for early pandas practice (loading, selecting, sorting)
- **Messy customer orders dataset** — the raw, uncleaned e-commerce dataset used in `Data_Cleaning.ipynb`
- **Cleaned customer orders dataset** — the final output after the full cleaning pipeline

## Purpose

This repo serves two goals:
1. A personal reference for pandas syntax and techniques as I build toward ML engineering
2. A portfolio piece demonstrating practical, real-world data cleaning skills for freelance data work

---
*Part of my ongoing self-directed learning journey in AI/ML engineering.*