workflows
=========

reusable github workflows / actions

## job templates

### .github/workflows/tox.yml


this job template will install python and invoke tox

#### parameters

- `env`: (json list of strings) the list of `tox` environment names to run
- `os`: (default: `ubuntu-latest`) passed through to [`runs-on`]
- `arch`: (json list of strings, default: '["x64"]') only used on windows to
  select the python executable
- `submodules`: (default: `false`) passed along to
  [`actions/checkout`]

this action auto-detects python versions via the env name.  here are some
examples:

- `py310`: will run with python 3.10
- `py310-wat`: will also run with python 3.10
- `pypy3`: will run using pypy 3.9
- `wat`: will run with python 3.11

[`runs-on`]: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idruns-on
[`actions/checkout`]: https://github.com/actions/checkout

#### example

```yaml
jobs:
  main:
    uses: heyslava/workflows/.github/workflows/tox.yml@v1.0.0
    with:
      env: '["py37", "py38", "pypy3"]'
```


#### Credits

Originally based on [asottile/workflows](https://github.com/asottile/workflows)
