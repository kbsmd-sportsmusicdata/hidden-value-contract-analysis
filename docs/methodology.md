# Methodology: WNBA Undervalued Contract Retrospective

## Data Sources

### Top-5 undervalued refresh panel

- File: `data/processed/top5_undervalued_panel.csv`
- Role: Preserves the five-player focus group across 2023-2025 seasons with basketball, value, trend, and scalability fields.
- Notes: The public repo keeps the evidence table but removes columns that were completely empty in this slice.

### 2026 contract status table

- File: `data/processed/wnba_2026_contract_status.csv`
- Role: Provides contract-year status, salary context, and roster-control framing.
- Notes: Useful for reading salary figures in the context of protections, options, and free-agency outcomes.

### 2024-2026 salary bridge

- File: `data/processed/wnba_2024_2026_salary_bridge.csv`
- Role: Links recent player performance context to next-season salary framing.
- Notes: Used to compare recent production and subsequent salary outcomes.

### 2026 team cap table

- File: `data/processed/wnba_2026_team_cap_table.csv`
- Role: Supplies team-level cap structure context.
- Notes: Helps frame player-level value inside a broader roster-construction environment.

### Upstream player-wide play-by-play working table

- File: not published in this slim repo
- Role: Upstream source used to build the five-player refresh panel and percentile-driven basketball metrics.
- Notes: Referenced for methodology transparency, but intentionally left out of the public bundle to keep the repo focused and lightweight.

## Public Repo Scope

This repo is intentionally notebook-first and slim. It ships the final HTML notebook plus four supporting evidence tables. It does not attempt to be a full reproducibility environment for every upstream working file, draft memo, or exploratory artifact used during the broader analysis process.

## Selection Logic

The retrospective keeps the original five-player focus group and asks a narrower question than the original project: which cases still hold up once 2026 market context is applied?

The working logic combines:

- Salary framing: actual 2026 salary versus expected salary and comparable-player salary context.
- Efficiency: true shooting and related scoring-quality indicators.
- Impact: on/off context and supporting percentile traits.
- Hidden value: tags that capture contribution beyond simple box-score volume.
- Scalability: a 10-point rubric that estimates whether value can hold if role or usage grows.

## Evidence Precedence

When the preferred season snapshot is available, the framework leans on that row first. If the ideal sample is unavailable, evidence precedence falls back in this order:

1. Same-season regular season
2. Same-season playoffs
3. Prior-season regular season
4. Prior-season playoffs

This keeps the notebook explicit about where the evidence came from instead of silently inferring unsupported updates.

## Cleaning And Curation Steps

- Restricted the public repo to four evidence tables and excluded heavier working files, draft markdowns, and scratch artifacts.
- Renamed shipped source files into portfolio-friendly processed filenames.
- Preserved the notebook as the source-of-truth deliverable rather than rebuilding the project as a dashboard.
- Removed columns that were entirely empty from the public `top5_undervalued_panel.csv` export so validation reflects the real evidence table rather than unused placeholders.

## Feature Engineering

- Compared actual 2026 salary against expected salary and comparable-player salary context.
- Tracked year-over-year efficiency, on/off, and trend labels within the retained five-player cohort.
- Carried forward a 10-point scalability score, confidence percentage, and supporting evidence notes to summarize upside and role portability.

## Core Metrics

### Primary Metrics

- **True Shooting Percentage**: Comprehensive scoring efficiency metric that incorporates two-point, three-point, and free-throw scoring.
- **On/Off Rating**: Team performance differential when the player is on the court versus off the court.
- **Expected Salary**: Model-side salary expectation used to compare a player's current 2026 salary against the framework's value estimate.

### Derived Metrics

- **Delta vs Comparable Salary**: 2026 salary minus comparable-player average salary.
- **Scalability Score**: 10-point rubric combining efficiency-to-usage signals, shot profile, on/off context, and supporting indicator slots.
- **Salary Change 2025 to 2026**: 2026 salary minus original 2025 salary reference.

## Modeling Approach

This is a rules-based decision-support framework, not a predictive machine learning model. The retrospective is built to support comparative judgment and prioritization, not to forecast future performance with a black-box score.

## Validation Checks

- Expected file presence check
- CSV row and column count check
- Duplicate row check
- Missing value summary

## Reproducibility Notes

This project uses a config-driven documentation workflow. Update `project_config.yml`, then regenerate docs using:

```bash
python scripts/generate_docs.py
python scripts/generate_readme.py
```

If you regenerate docs after adding the GitHub Pages URL, reapply any project-specific editorial polish that lives outside the base templates.
