
# Postgres

Django supports PostgreSQL 9.6 and higher. psycopg2 2.5.4 or higher is required, though the latest release is recommended.

## Installation

Install psycopg2 with pipenv

```bash
pipenv install psycopg2
```

If installing psycopg2 fails with the following error

```text
Installing psycopg2...
Error:  An error occurred while installing psycopg2!
Error text: Collecting psycopg2
  Downloading psycopg2-2.9.3.tar.gz (380 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 380.6/380.6 kB 1.9 MB/s eta 0:00:00
  Preparing metadata (setup.py): started
  Preparing metadata (setup.py): finished with status 'error'

  error: subprocess-exited-with-error

  × python setup.py egg_info did not run successfully.
  │ exit code: 1
  ╰─> [25 lines of output]
      running egg_info
      creating /tmp/pip-pip-egg-info-3uy42pe5/psycopg2.egg-info
      writing /tmp/pip-pip-egg-info-3uy42pe5/psycopg2.egg-info/PKG-INFO
      writing dependency_links to /tmp/pip-pip-egg-info-3uy42pe5/psycopg2.egg-info/dependency_links.txt
      writing top-level names to /tmp/pip-pip-egg-info-3uy42pe5/psycopg2.egg-info/top_level.txt
      writing manifest file '/tmp/pip-pip-egg-info-3uy42pe5/psycopg2.egg-info/SOURCES.txt'
      /home/kitty/kitty/django-web/.venv/lib/python3.8/site-packages/setuptools/config/setupcfg.py:463: SetuptoolsDeprecationWarning: The license_file parameter is deprecated, use license_files instead.
        warnings.warn(msg, warning_class)

      Error: pg_config executable not found.

      pg_config is required to build psycopg2 from source.  Please add the directory
      containing pg_config to the $PATH or specify the full executable path with the
      option:

          python setup.py build_ext --pg-config /path/to/pg_config build ...

      or with the pg_config option in 'setup.cfg'.

      If you prefer to avoid building psycopg2 from source, please install the PyPI
      'psycopg2-binary' package instead.

      For further information please check the 'doc/src/install.rst' file (also at
      <https://www.psycopg.org/docs/install.html>).

      [end of output]

  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
╰─> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.

This is likely caused by a bug in psycopg2. Report this to its maintainers.
✘ Installation Failed
```

Please Install psycopg2-binary with pipenv

```bash
pipenv install psycopg2-binary
```

or Installing dependencies solved it for me

```bash
sudo apt-get install libpq-dev
pipenv install psycopg2
```

If you have used `django-environ`

In `.env` setting:

```text
DATABASE_URL=postgres://user:password@host:port/dbname
```
