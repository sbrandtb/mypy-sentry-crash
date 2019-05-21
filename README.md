# mypy-sentry-crash
Minimal example for demonstrating an internal error in mypy


## How-To

```shell
pipenv install --dev
pipenv shell

$ MYPYPATH=`pipenv --venv`/lib/python3.7/site-packages/ mypy .

path/to/site-packages/sentry_sdk/consts.py:13: error: INTERNAL ERROR -- please report a bug at https://github.com/python/mypy/issues version: 0.701
path/to/site-packages/sentry_sdk/consts.py:13: : note: please use --show-traceback to print a traceback when reporting a bug

$ MYPYPATH=`pipenv --venv`/lib/python3.7/site-packages/ mypy . --tb

path/to/site-packages/sentry_sdk/consts.py:13: error: INTERNAL ERROR -- please report a bug at https://github.com/python/mypy/issues version: 0.701
Traceback (most recent call last):
  File "path/to/bin/mypy", line 10, in <module>
    sys.exit(console_entry())
  File "mypy/semanal.py", line 3791, in accept
  File "mypy/nodes.py", line 1018, in accept__Node_glue
  File "mypy/nodes.py", line 1019, in accept
  File "mypy/semanal.py", line 1762, in visit_assignment_stmt__StatementVisitor_glue
  File "mypy/semanal.py", line 1774, in visit_assignment_stmt
  File "mypy/semanal_typeddict.py", line 156, in process_typeddict_definition
  File "mypy/semanal_typeddict.py", line 202, in check_typeddict
  File "mypy/semanal_typeddict.py", line 279, in build_typeddict_typeinfo
AssertionError:
path/to/site-packages/sentry_sdk/consts.py:13: : note: use --pdb to drop into pdb
```
