# Copilot Instructions

This is a documentation-only repository for Google Search URL parameters.

## Key Facts

- 62 total parameters: 18 Chromium tokens, 3 standard, 18 fixed, 15 advanced, 8 tracking
- `num` is DEAD (Sep 2025) — do not recommend it
- `tbm` is LEGACY — always suggest `udm` instead
- `gs_lcrp` has replaced `aqs` (Chromium commit, Mar 2022)
- `as_rq` is ZOMBIE — present in URLs but non-functional
- Status legend: ✅ active, ⚠️ legacy, ☠️ dead, 🧟 zombie

## When Generating URLs

- Always include `q=%s` or `q=<terms>`
- Use `gl=IN` unless user specifies otherwise
- Mark dead/zombie params if included
- Output as a code block

## When Editing Tables

- Keep `params.csv` and `docs/params.md` in sync
- Column order in CSV: category, param_or_token, default_value, resolves_to, description, status, notes
- Use GFM table format in markdown   
