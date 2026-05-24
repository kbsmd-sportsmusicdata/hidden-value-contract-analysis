# Project Handoff: WNBA Undervalued Contract Retrospective

## Current Status

in-progress

## Project Purpose

This project revisits a five-player undervalued contract cohort to test which cases still hold up once the original hidden-value lens is reframed against 2026 salary levels, comparable-player context, and role-scalability evidence.

## Key Deliverables

- Primary deliverable: HTML notebook
- Notebook: `notebooks/index.html`
- Executive summary: `docs/executive_summary.md`
- Methodology: `docs/methodology.md`
- Data dictionary: `docs/data_dictionary.md`
- Validation report: `docs/validation_report.md`

## Important Scripts

- `scripts/init_project.py`
- `scripts/generate_docs.py`
- `scripts/generate_readme.py`
- `scripts/validate_data.py`
- `scripts/publish_check.py`

## Known Limitations

- This public repo ships a slim evidence bundle rather than the full upstream working environment.
- Some retrospective judgments rely on the latest supported 2023-2025 row when a preferred 2025 sample is unavailable.
- Contract framing is tied to the 2026 salary and roster-control context captured in the shipped evidence tables.

## Next Steps

- Backfill the live GitHub Pages URL into project_config.yml after deployment.
- Add lightweight branch protection after the first successful private deployment.
- Extend the repo with player-level briefs only if a broader public story is needed.

## Deployment Notes

GitHub Pages should deploy `notebooks/index.html` through the workflow in `.github/workflows/deploy_pages.yml`.
