# Copilot Instructions for this repository

This repository is a small, notebook-first data analysis project focused on health study CSVs. The goal of these instructions is to help AI coding agents be immediately productive by documenting project shape, conventions, and common developer workflows.

Key files and artifacts
- `README.md`: minimal environment note (Python 3.11.9).
- `requirements.txt`: dependency pins used for reproducing the environment.
- `data/data_health2.ipynb`: primary analysis notebook to read and extend.
- `data/health_study_dataset.csv`, `data/statistics_health.csv`: source CSVs used by the notebooks.

High-level architecture (big picture)
- Single-purpose data analysis repo — not a package or service. Work is performed inside Jupyter notebooks under `data/`.
- Data flow: CSV files in `data/` -> loaded with `pandas.read_csv()` inside notebooks -> transformations and figures are produced inline.
- There are no background services, web servers, or CI tests in the repository (no `src/` package or `tests/` directory present).

Developer workflows (explicit commands & examples)
- Create and activate a virtual environment (Windows PowerShell):
  - `python -m venv .venv`
  - `.\.venv\Scripts\Activate.ps1`
  - `pip install -r requirements.txt`
- Open the primary notebook in Jupyter:
  - `jupyter notebook data/data_health2.ipynb`
  - Or open the notebook in VS Code's Notebook editor.
- If you need to run code cells programmatically, convert notebook to a script or use `nbconvert`.

Project-specific conventions and patterns
- Notebooks are the canonical source of analysis and should be updated in-place. Prefer small, focused cells and keep data-loading cells at the top.
- Raw CSVs live in `data/`. When modifying data files, preserve original filenames; add new files with descriptive names (e.g., `data/processed_*.csv`).
- Use `pandas` for I/O and transformations. Expect patterns like `pd.read_csv('data/health_study_dataset.csv')`.
- No unit tests or packaging established — changes should be validated by re-running the notebook cells and checking outputs/figures.

Integration points & external dependencies
- External integrations: none discovered. Dependencies are in `requirements.txt`; inspect it before adding new packages.
- If code needs to be refactored into importable modules, create a `src/` or `package` folder and add a minimal `__init__.py`.

How Copilot/AI should operate here
- Focus on: editing and clarifying notebook cells, adding helper Python modules when code is reused, and updating `requirements.txt` if adding packages.
- Avoid creating heavy scaffolding or service code — this repo is analysis-first.
- When proposing changes that affect data, include the exact `data/` paths and an explanation of how the notebook outputs will change.

Examples from this repo to reference in suggestions
- To add a reproducible environment section, update `README.md` and include the exact commands above.
- To extend analysis, add a new notebook `data/data_health2_v2.ipynb` or create a helper script `data/helpers.py` that is imported by the notebook.

If anything in these instructions is unclear or you want a different focus (e.g., turning this into a Python package or adding tests), say so and I will iterate.
