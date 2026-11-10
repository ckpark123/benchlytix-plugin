# Eval results

Only dated summaries are committed here:

- `<date>-panel.md`: the T11 trigger panel (trigger rate and false triggers per group).
- `<date>-pass<n>.md`: one eval pass (cases passed and score per stage, the delta check, cost, model ids).

The spend ledger is not here: it is one file outside every checkout, `~/.benchlytix/plugin-evals/ledger.jsonl` in the
source repository's operator account, so no branch or worktree starts a fresh budget ($200 in total, the panel
included; $60 for pass 1, calibration included).

Each run's `aggregate-result.json` and `report.html` hold prompts, answers and transcripts. They stay in
`results/<timestamp>-*/`, which is ignored and never synced to the mirror. Never point evals at production: the
mock tier answers from `evals/mocks`, and the live tier runs against a local server built from a clean export.
