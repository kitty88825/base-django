# Commitizen

Commitizen is a tool designed for teams.

Its main purpose is to define a standard way of committing rules and communicating it (using the cli provided by commitizen).

The reasoning behind it is that it is easier to read, and enforces writing descriptive commits.

Besides that, having a convention on your commits makes it possible to parse them and use them for something else, like generating automatically the version or a changelog.

## Installation

Install commitizen with pipenv

```bash
pipenv install commitizen --dev
```

## Usage/Examples

### Committing

```shell
cz commit
```

or the shortcut

```shell
cz c
```

### Integrating with Pre-commit

Commitizen can lint your commit message for you with `cz check`.
You can integrate this in your [pre-commit](https://pre-commit.com/) config with:

```yaml
repos:
  - repo: https://github.com/commitizen-tools/commitizen
    rev: master
    hooks:
      - id: commitizen
```

After the configuration is added, you'll need to run

```sh
pre-commit install --hook-type commit-msg
```

## Documentation

GitHub: <https://github.com/commitizen-tools/commitizen>

PyPI: <https://pypi.org/project/commitizen/>

Documentation: <https://commitizen-tools.github.io/commitizen/>
