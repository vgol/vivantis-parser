# Copilot Instructions

## Project Overview

`vivantis-parser` is a Python-based B2B supplier parser. All code is written in Python and managed with **uv**.

## Toolchain

- **Package manager / runtime**: [uv](https://docs.astral.sh/uv/) — use `uv run`, `uv add`, `uv remove`, `uv sync`, etc. Never use `pip` directly, and never use `uv pip` subcommands.
- **Formatter & linter**: [ruff](https://docs.astral.sh/ruff/) — run `uv run ruff format .` to format and `uv run ruff check --fix .` to lint.
- **Type checker**: [ty](https://github.com/astral-sh/ty) — run `uv run ty check` to type-check the project.
- **Editor**: Visual Studio Code with the official [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) (Pylance / python-language-server).

## Code Style

- Follow **PEP 8**; formatting is enforced by ruff.
- Use **type annotations** on all function signatures and class attributes. Keep types precise so `ty` can verify them statically.
- Never use `from __future__ import annotations`; this project targets Python 3.14 and does not need it.
- Use **f-strings** for string interpolation.
- Keep functions small and focused; extract helpers when a function exceeds ~30 lines.
- Avoid bare `except:`; always catch specific exception types.
- Do not suppress type errors with `# type: ignore` unless absolutely necessary, and always add an explanatory comment when you do.

## Project Structure Conventions

- Source code lives under `src/vivantis_parser/` (or the package root configured in `pyproject.toml`).
- Tests live under `tests/` and use **pytest**.
- Configuration for ruff, ty, and other tools belongs in `pyproject.toml` under the appropriate `[tool.*]` sections.

## Dependency Management

- Add runtime dependencies with `uv add <package>`.
- Add development/tooling dependencies with `uv add --dev <package>`.
- Never edit `uv.lock` manually.

## Testing

- Run the test suite with `uv run pytest`.
- Aim for meaningful test coverage; use `pytest-cov` when coverage reporting is needed.
- Tests should be deterministic and not depend on external network calls — mock HTTP clients where needed.

## Common Commands

```bash
# Install all dependencies
uv sync

# Format code
uv run ruff format .

# Lint and auto-fix
uv run ruff check --fix .

# Type-check
uv run ty check

# Run tests
uv run pytest
```
