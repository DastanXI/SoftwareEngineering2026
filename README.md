# Expense Tracker

Small CLI to record expenses and print totals.

## Setup
    pip install -r requirements.txt

## Usage
    python -m expense_tracker add 10 food lunch
    python -m expense_tracker total
    python -m expense_tracker summary
    python -m expense_tracker export csv|json|text

Data is stored in `expenses.json` (override with the `EXPENSE_FILE` environment variable).

## Development
    python -m pytest -q
    ruff check .

See `AGENTS.md` for agent instructions and `ACCEPTANCE.md` for acceptance criteria.
