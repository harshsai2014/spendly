# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Spendly — a Flask expense tracker built as a step-by-step student project. Many parts are intentionally stubbed with "coming in Step N" placeholders; implement them only when asked.

## Commands

```bash
python -m venv venv && venv\Scripts\activate   # venv/ is gitignored
pip install -r requirements.txt                # flask, werkzeug, pytest, pytest-flask
python app.py                                  # dev server, debug mode, http://localhost:5001
pytest                                         # run tests (no tests exist yet)
pytest path/to/test_file.py::test_name         # run a single test
```

No linter or build step is configured.

## Architecture

- `app.py` — single Flask app; all routes live here. Implemented routes (`/`, `/register`, `/login`, `/terms`, `/privacy`) only render templates (no form handling yet). `/logout`, `/profile`, `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete` return placeholder strings.
- `database/db.py` — currently only a comment stub describing the planned `get_db()` (SQLite connection with `row_factory` and foreign keys on), `init_db()` (`CREATE TABLE IF NOT EXISTS`) and `seed_db()`. The DB file `expense_tracker.db` is gitignored.
- `templates/` — all pages extend `base.html` (navbar, `content`/`title`/`head` blocks, footer).
- `static/css/` — `base.html` loads **both** `style.css` and `landing.css`, in that order. `style.css` holds the global design tokens (CSS variables such as `--accent`, `--paper`, `--max-width`) and shared component rules, including `.hero*`. `landing.css` deliberately **overrides** the shared `.hero*` rules for the landing page's centered single-column hero, so hero changes usually need edits in `landing.css` and must account for cascade against `style.css`.
- `static/js/main.js` — empty placeholder.

## Conventions

- Commit messages for landing page work use the prefix `landing: ` (e.g. `landing: redesign hero section to match mockup`).
- When a task says to change only a specific section (e.g. the hero), leave the rest of the page and CSS untouched.
