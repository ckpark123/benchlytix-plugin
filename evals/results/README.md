# Eval results

Only dated summaries are committed here:

- `<date>-panel.md`: the T11 trigger panel (trigger rate and false triggers per group).
- `<date>-pass<n>.md`: one eval pass (cases passed and score per stage, the delta check, model ids).

Spending on eval runs is tracked outside this repository and is not part of these summaries.

Each run's `aggregate-result.json` and `report.html` hold prompts, answers and transcripts. They stay in
`results/<timestamp>-*/`, which is ignored and never synced to the mirror. Never point evals at production: the
mock tier answers from `evals/mocks`, and the live tier runs against a local server built from a clean export.
