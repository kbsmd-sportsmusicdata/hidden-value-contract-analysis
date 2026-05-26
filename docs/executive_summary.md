# Executive Summary: WNBA Hidden Value Contract Retrospective

## Project Objective

This project revisits an original five-player undervalued contract cohort (compiled and analyzed for an assignment in my Basketball Analytics class) to test which cases still hold up once the original hidden-value lens is reframed against an additional season of stats, updated salary levels, comparable-player context, role-scalability evidence, and retrospective performance signals.

The original cohort included Leonie Fiebich, Emily Engstler, Naz Hillmon, Nyara Sabally, and Jordan Horston. For the final retrospective scoring layer, the notebook focuses on four scored players — Fiebich, Engstler, Hillmon, and Sabally — while treating Horston as an incomplete injury-context case as she was out due to injury during the 2025 season.

The goal is not to prove every original pick was right. The goal is to show how the original undervalued-contract read changed once additional salary, performance, comp, and scalability evidence became available.

## Intended Audience

* WNBA front office decision-makers
* Salary cap and roster strategy staff
* Scouting and player development staff
* Sports analytics portfolio reviewers

## Key Questions

* Which originally flagged undervalued players still grade as salary surplus after updated comp and cap-share context?
* Which players show scalable hidden value even when market pricing has partially corrected?
* Which cases now read as fair market, market-corrected, incomplete, or higher-risk bets?
* Where did the original model hold up, and where did the retrospective evidence complicate the original claim?

## Decision-Support Value

The notebook gives decision-makers a compact way to compare contract surplus, comparable-player pricing, cap-share cost, role scalability, and performance validation in the same frame.

Instead of treating all original picks as equal bargains, the retrospective separates retained surplus from corrected pricing and mixed evidence. That makes the analysis more useful for real roster-building questions: who still looks like an acquisition value, who has already been priced closer to market, and which cases need more 2026 evidence before making a stronger claim.

## Validation Approach

The retrospective uses two salary-validation windows:

1. **Cleaner validation: 2024 stats → 2025 salary**
   This is the most direct test of whether the original undervalued signal was directionally supported in the next salary window.

2. **Market reset check: 2025 stats → 2026 salary**
   This adds a follow-up layer, but it is treated as contextual rather than perfect ground truth because the 2026 WNBA salary environment changed substantially.

For 2026, the notebook emphasizes **median comparable-player salary** and **cap-share normalization** rather than raw salary movement alone. This helps avoid overstating salary changes that may reflect leaguewide market shifts rather than purely player-specific valuation.

Role-scalability evidence is used as a supporting layer. It helps explain whether a player’s production profile appears likely to hold up with a larger role, but it does not replace the salary-gap and cap-share validation logic.

## Top Findings

### Leonie Fiebich remains the cleanest retained surplus case.

Fiebich is the strongest validation hit in the retrospective. Her efficiency and impact profile still hold up, and the 2026 cap-share view shows the clearest gap between her salary cost and her comparable-player market. She remains the most straightforward example of a player whose contract still appears meaningfully below the value suggested by her comp context and scalable skill profile.

### Emily Engstler grades as a strong hidden-value hit through versatility rather than scoring.

Engstler’s case is not built around pure scoring growth. Her value comes through defensive versatility, stocks, passing, rebounding activity, and role flexibility. The refreshed evidence still supports the original undervalued thesis because her salary remains below comparable-player pricing while her profile continues to offer multi-category impact.

### Naz Hillmon looks market-corrected, but still validated.

Hillmon’s 2026 salary increase suggests the market recognized more of her value. That makes her less of a pure bargain than the original version of the project suggested. However, her role growth, improved performance indicators, and remaining cap-share gap versus comparable players keep her in the validated column. She is best framed as a market-corrected hit rather than a still-obvious discount.

### Nyara Sabally is the most mixed case.

Sabally’s original 2025 salary signal was supported, but the 2026 comparison is more complicated. Her updated salary now sits above the median comp frame in the refreshed analysis, while the 2025 performance signal is more mixed. She remains a useful role-player value case, but the retrospective should treat her as a partial miss or a player requiring a 2026 check-in rather than as a clean retained surplus case.

### Jordan Horston is treated as an incomplete case.

Horston was part of the original undervalued cohort, but is excluded from the main retrospective scoring layer due to injury throughout the 2025 season, therefore having no on-court data sample and preventing the same validation framework from being applied. Her original case remains worth tracking, but it should not be scored alongside the four players with more complete retrospective evidence.

## Final Retrospective Labels

| Player         | Final Retrospective Label                          | Summary Read                                                                                          |
| -------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Leonie Fiebich | Strong Hit — Still Significantly Undervalued       | Cleanest retained surplus case; strong cap-share and comp gap signal.                                 |
| Emily Engstler | Strong Hit — Underpaid Versatility Value           | Hidden value remains supported through defense, passing, rebounding, and role flexibility.            |
| Naz Hillmon    | Hit — Market-Corrected, Still Slightly Under Comps | Salary moved closer to market, but role growth and comp context still validate the original read.     |
| Nyara Sabally  | Mixed / Partial Miss — Needs 2026 Check-In         | Original signal was supported, but refreshed salary and performance context make the case less clean. |
| Jordan Horston | Incomplete — Injury Context                        | Removed from main scoring because the 2025 validation sample is unavailable.                          |

## Recommended Use Cases

* Contract surplus review
* Rotation value triage
* Minutes scalability evaluation
* Comparable-player salary review
* Retrospective model critique
* Sports analytics portfolio demonstration

## Limitations

* This public repo ships a slim evidence bundle rather than the full upstream working environment.
* The final scoring framework focuses on four players because Jordan Horston did not have a usable 2025 on-court sample for the same retrospective test.
* Some retrospective judgments rely on the latest supported 2023–2025 row when a preferred 2025 sample is unavailable.
* The 2026 WNBA salary environment should be interpreted as a market reset rather than a clean continuation of the 2025 salary structure.
* Expansion, widespread free agency, and new salary rules can distort raw 2025-to-2026 salary comparisons, which is why the notebook also uses median comp salary and cap-share normalization.
* Role-scalability evidence is directional and should be treated as context, not as a standalone salary valuation model.

## Bottom Line

The retrospective strengthens the original project because it does not simply repeat the original undervalued claims. It tests them.

Fiebich and Engstler emerge as the clearest hits. Hillmon becomes a market-corrected but still validated case. Sabally becomes the honest mixed result. Horston is removed from the main scoring layer because injury prevents a fair comparison.

That makes the final notebook a stronger portfolio piece: it shows the full analytics workflow of making a player-value claim, defining a validation test, revisiting the evidence, and updating the conclusion when the market and player context change.
