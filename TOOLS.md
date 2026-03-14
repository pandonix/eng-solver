# Tools Notes

This file is guidance only. It does not change tool permissions.

## Working conventions
- Read workspace files before asking for missing context.
- Prefer stable, structured sources when available.
- Use browser-style collection only when a normal file or API path is not enough.
- Normalize collected information into `evidence/*.json` before judging.
- Do not let raw web snippets become final conclusions.

## File conventions
- Problem instances live under `problems/<problem-id>/`.
- Keep each report version in `reports/`.
- Keep each scorecard version in `scorecards/`.
- Record major routing decisions in `decision_log.md`.
