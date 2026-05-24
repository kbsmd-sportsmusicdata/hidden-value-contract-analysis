# Data Dictionary: WNBA Undervalued Contract Retrospective

## Overview

This document defines the core public fields used in the slim evidence bundle that supports the notebook.

## `data/processed/top5_undervalued_panel.csv`

Five-player retrospective panel with basketball, value, and scalability fields across the retained 2023-2025 evidence window.

| Field | Type | Description | Source | Calculation Logic | Notes |
|---|---|---|---|---|---|
| `Name` | string | Player name | Refresh panel | Direct from upstream player record | Five-player focus cohort only |
| `Season` | integer | Basketball season used for the evidence row | Refresh panel | Direct season field | May use latest supported season when preferred snapshot is unavailable |
| `TeamAbbreviation` | string | Team abbreviation for the evidence row | Refresh panel | Direct from upstream team record | Context field |
| `Minutes` | float | Minutes played in the retained season row | Refresh panel | Direct from upstream statistics | Helps frame sample size |
| `TsPct` | float | True shooting percentage | Refresh panel | Points divided by shooting possessions adjustment | Primary efficiency signal |
| `Usage` | float | Usage rate | Refresh panel | Possession-share usage metric | Used in scalability framing |
| `OnOffRtg` | float | On/off rating | Refresh panel | Team performance differential with player on court | Primary impact context |
| `salary` | float | Current salary used in the 2026 framing layer | Contract bridge into refresh panel | Direct linked salary field | Current contract context |
| `expected_salary` | float | Model-side expected salary estimate | Value model output | Framework-derived expected salary | Used to compare actual versus modeled value |
| `delta_vs_comp_salary_2026` | float | Difference between player salary and comparable-player average | Comparable salary layer | `salary - avg comparable salary` | Negative values indicate below-comp pricing |
| `comp_salary_relation_2026` | string | High-level comp read | Comparable salary layer | Label from comp delta sign and thresholds | Examples: `below comps`, `above comps` |
| `scalability_score_10pt` | float | 10-point scalability score | Scalability rubric | Aggregated indicator slots | Higher is better |
| `scalability_confidence_pct` | integer | Confidence percentage for scalability interpretation | Scalability rubric | Confidence output from scored indicator coverage | Used with score and rating label |
| `scalability_rating_label` | string | Human-readable scalability grade | Scalability rubric | Label mapped from score band | Examples: `High`, `Good`, `Moderate` |
| `value_label` | string | High-level value interpretation | Value model output | Label mapped from value logic | Used in notebook summary framing |
| `trend_label_hidden_value` | string | YoY hidden-value trend label | Refresh trend layer | Label based on retained trend rules | Examples: `improved`, `stable` |

## `data/processed/wnba_2026_contract_status.csv`

Contract-status evidence table used for roster-control and salary framing.

| Field | Type | Description | Source | Calculation Logic | Notes |
|---|---|---|---|---|---|
| `team` | string | Team name | Contract status table | Direct source field | Used for team-level filtering |
| `team_slug` | string | Team slug | Contract status table | Direct source field | Normalized team identifier |
| `player` | string | Player name | Contract status table | Direct source field | Contract row subject |
| `year` | integer | Contract year | Contract status table | Direct source field | Usually 2026+ |
| `salary` | float | Salary amount for the contract year | Contract status table | Direct source field | Can be null for future unresolved rows |
| `pct_cap` | float | Share of team cap used by the salary | Contract status table | `salary / salary_cap` | Only present when enough team context is available |
| `pct_team` | float | Share of team salary pool | Contract status table | Salary divided by tracked team total | Supplemental roster-cost context |
| `contract_icon` | string | Human-readable contract bucket | Contract status table | Derived or inferred contract label | Includes protections and inferred statuses |
| `status` | string | Free-agency or roster-control status | Contract status table | Direct or derived status field | Examples include `UFA`, `RFA`, `Reserved` |
| `status_full` | string | Expanded status description | Contract status table | Narrative version of status | Often blank when not needed |

## `data/processed/wnba_2024_2026_salary_bridge.csv`

Bridge table linking recent performance context to next-season salary framing.

| Field | Type | Description | Source | Calculation Logic | Notes |
|---|---|---|---|---|---|
| `season` | integer | Source performance season | Salary bridge | Direct source field | Anchor season for the bridge |
| `player_name` | string | Player name | Salary bridge | Direct source field | Used for joins and comparison |
| `season_plusone_salary_usd` | float | Next-season salary amount | Salary bridge | Direct source field | Connects performance season to contract outcome |
| `season_plusone_signing` | string | Signing or contract descriptor | Salary bridge | Direct source field | Qualitative contract context |
| `games_played` | integer | Games played in the source season | Salary bridge | Direct source field | Sample-size context |
| `minutes_total` | integer | Total minutes in the source season | Salary bridge | Direct source field | Volume context |
| `PER` | float | Player efficiency rating | Salary bridge | Direct source field | Supplemental performance metric |
| `win_shares` | float | Win shares | Salary bridge | Direct source field | Supplemental value metric |
| `player_off_rtg` | float | Offensive rating | Salary bridge | Direct source field | Supplemental context field |
| `player_def_rtg` | float | Defensive rating | Salary bridge | Direct source field | Supplemental context field |

## `data/processed/wnba_2026_team_cap_table.csv`

Team-level cap structure reference used to frame player value inside roster-building constraints.

| Field | Type | Description | Source | Calculation Logic | Notes |
|---|---|---|---|---|---|
| `season` | integer | Cap season | Team cap table | Direct source field | Current table is focused on 2026 |
| `team_name` | string | Team name | Team cap table | Direct source field | Team identifier |
| `team_slug` | string | Team slug | Team cap table | Direct source field | Normalized team identifier |
| `salary_cap` | float | Team salary cap | Team cap table | Direct source field | Core denominator for cap shares |
| `total_cap_hit` | float | Total cap hit for tracked salaries | Team cap table | Aggregated team total | Used to measure cap usage |
| `cap_space` | float | Remaining cap space | Team cap table | `salary_cap - total_cap_hit` | Roster flexibility context |
| `cap_used_pct` | float | Cap usage percentage | Team cap table | `total_cap_hit / salary_cap` | Quick roster pressure indicator |
| `total_players` | integer | Players counted in the table | Team cap table | Direct source field | Team roster context |
| `open_roster_slots` | integer | Remaining roster slots | Team cap table | Derived roster count field | Helps frame flexibility |
| `top_3_salary_share` | float | Share of cap concentrated in top three salaries | Team cap table | Derived concentration field | Useful for roster concentration reads |
| `top_5_salary_share` | float | Share of cap concentrated in top five salaries | Team cap table | Derived concentration field | Useful for roster concentration reads |
| `validation_pass` | boolean | Whether the source cap checks passed | Team cap table | Validation flag from source workflow | Helps trust the published table |

## Primary Metrics

### True Shooting Percentage

- Definition: Comprehensive scoring efficiency metric that incorporates two-point, three-point, and free-throw scoring.
- Interpretation: Higher values indicate more efficient scoring quality for the player role and shot diet.

### On/Off Rating

- Definition: Team performance differential when the player is on the court versus off the court.
- Interpretation: Positive or stronger relative values suggest impact that may not fully appear in traditional box-score volume.

### Expected Salary

- Definition: Model-side salary expectation used to compare a player's current 2026 salary against the framework's value estimate.
- Interpretation: A higher expected salary than actual salary suggests retained surplus value.

## Derived Metrics

### Delta vs Comparable Salary

- Formula: `salary - avg comparable salary`
- Interpretation: Negative values suggest the player is priced below the selected comparable set.

### Scalability Score

- Formula: 10-point rubric combining efficiency-to-usage signals, shot profile, on/off context, and supporting indicator slots.
- Interpretation: Higher scores suggest better odds that value can hold if the role grows.

### Salary Change 2025 to 2026

- Formula: `2026 salary - original 2025 salary reference`
- Interpretation: Shows how much of the original undervaluation thesis has already been priced into the current market.
