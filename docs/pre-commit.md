
# Pre-Commit

A framework for managing and maintaining multi-language pre-commit hooks.

## Installation

Install pre-commit with pipenv

```bash
pipenv install pre-commit --dev
```

## Quick start

### Create config file

Create `.pre-commit-config.yaml` file:

```yaml
exclude: '^$'

repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v2.3.0
    hooks:
      - id: check-yaml
      - id: end-of-file-fixer
      - id: trailing-whitespace
  - repo: https://github.com/psf/black
    rev: 22.3.0
    hooks:
      - id: black
  - repo: https://github.com/pycqa/isort
    rev: 5.10.1
    hooks:
      - id: isort
        name: isort (python)
  - repo: https://github.com/pycqa/flake8
    rev: 4.0.1
    hooks:
      - id: flake8

```

### Install the git hook scripts

```bash
pre-commit install
```

### (optional) Run against all the files

```bash
pre-commit run --all-files
```

## Documentation

Documentation: <https://pre-commit.com/>
