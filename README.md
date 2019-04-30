# django-test-commit-hook

## Config

**IMPORTANT**

This pre-commit hook creates a virtualenv named PRE_COMMIT_VENV. Ensure that your *.gitignore* has been updated to ignore this directory. For example:

```
# Ignore django-test-commit-hook virtualenv
PRE_COMMIT_ENV
```

Add the following to your .pre-commit-config.yaml file:

```yaml
- repo: https://github.com/dotmodusgeorge/django-test-commit-hook
  rev: v0.0.3
  hooks:
    - id: django-commit-tester
      args:
      - --testdir=myproj/automated_tests
      - --managedir=myproj
      - --requirements=proj/requirements.txt
      language_version: python3
```

The three arguments are required and allude to:

**testdir** - The directory where the unit tests are stored

**managedir** - The directory containing the manage.py file for the Django project

**requirements** - Relative path to the file containing the PIP packages to be installed

To streamline the process, you can create a virtual env named PRE_COMMIT_VENV in the same directory as the pre-commit-config.yaml file. 

```bash

virtualenv PRE_COMMIT_VENV

source PRE_COMMIT_VENV/bin/activate

pip install -r {YOU_REQUIREMENTS_FILE.txt}

```
