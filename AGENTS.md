# AGENTS.md

This repository is a **documentation-only reference** for Google Search URL parameters. There is no executable code, no build system, and no tests.

## What This Repo Contains

- `template.txt` — The full Chromium search template (54 elements)
- `params.csv` — Machine-readable 62-row parameter table
- `docs/` — Categorized markdown reference (tokens, fixed, advanced, tracking, sub-values)
- `examples/` — Working URL strings for common use cases
- `presets/` — Named template strings for browser settings
- `llms.txt` / `llms-full.txt` — LLM-readable index and full content

## Rules for Agents

1. **No code to build or test.** Do not attempt to run, lint, or build anything.
2. **Status matters.** Every parameter has a status: `active`, `legacy`, `dead`, `zombie`. Never present a `dead` or `zombie` param as functional without noting its status.
3. **`num` is dead.** As of Sep 2025, Google ignores `num`. Always flag it if referenced.
4. **`tbm` is legacy.** Always recommend `udm` as the replacement.
5. **`gs_lcrp` replaces `aqs`.** Do not present both as active simultaneously.
6. **Keep CSV in sync.** If you modify `docs/params.md`, update `params.csv` to match (same 62 rows, same column order).
7. **Date your claims.** Statuses are point-in-time. Use the format "as of Nov 2026" when stating a param's status.
8. **Do not fabricate params.** Only include parameters that have been observed in a live Google Search URL or confirmed in Chromium source.

## File Conventions

- All markdown files use GitHub Flavored Markdown (GFM) tables
- Status emojis: ✅ active, ⚠️ legacy, ☠️ dead, 🧟 zombie
- Template strings use `{google:...}` tokens exactly as Chromium defines them
- CSV column order: `category,param_or_token,default_value,resolves_to,description,status,notes`

## Verification

To verify a parameter is still active:
1. Perform a search in Chrome with the param in the URL
2. Check if the param appears in the final SERP URL
3. Check if it changes the result set
4. Update `CHANGELOG.md` with the date and finding

## Suggested Workflow

When asked to add a new parameter:
1. Confirm it appears in a live Google Search URL (not just documentation)
2. Determine its status (active/legacy/dead/zombie)
3. Add a row to `params.csv`
4. Add the row to the appropriate table in `docs/params.md`
5. Add a note to `CHANGELOG.md`
6. Update `llms-full.txt` if the param affects the template   
