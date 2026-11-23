# AGENTS.md - instructions for AI coding agents

## Purpose
Expense Tracker: a tiny Python 3.12 CLI that records expenses in a local JSON file and prints totals,
per-category summaries and exports (csv/json/text). Educational project; contains no real personal data.

## Architecture
- `expense_tracker/cli.py`      argparse entry point (`python -m expense_tracker ...`). No business logic.
- `expense_tracker/tracker.py`  business logic: add, total, summary, export dispatch.
- `expense_tracker/exporters.py` one function per export format + `EXPORTERS` registry.
- `expense_tracker/storage.py`  JSON persistence (`EXPENSE_FILE` env var, default `./expenses.json`).
- `tests/`                      pytest suite. `ACCEPTANCE.md` lists AC1-AC5 that must keep passing.

## Setup
    python -m venv .venv && source .venv/bin/activate
    pip install -r requirements.txt

## Safe commands (run freely)
    python -m pytest -q
    ruff check .
    python -m expense_tracker total        # only with EXPENSE_FILE pointing to a temp file
    git status / git diff / git log

## Coding conventions
- Python 3.12, type hints encouraged, line length 100, ruff rules E,F,I must pass.
- Keep CLI free of business logic. New export format = one function + one `EXPORTERS` entry.
- Never use bare `except:`; raise specific errors.
- Every behaviour change needs a test; do not weaken or delete existing tests to make them pass.

## Test expectations
`python -m pytest -q` and `ruff check .` must both pass before any commit. Report exact pass/fail
counts; never claim a check passed without running it.

## Forbidden actions
- No secrets, tokens or real personal/financial data in code, tests, logs or commits.
- No production deployment, publishing, or pushing to remote branches without human approval.
- No destructive commands: `rm -rf`, `git reset --hard`, `git push --force`, deleting `.git`, overwriting
  a user's real `expenses.json`.
- No adding, removing or upgrading dependencies without explicit human review.
- No network calls or installs other than `pip install -r requirements.txt`.

## Review gates
Agent changes are proposed as a diff on a separate branch. A human reviews the diff and the test output
before merge. Out-of-scope edits (files not named in the task) must be flagged, not made.
