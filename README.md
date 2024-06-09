# action-find-files

A Github Action to find files.

## Usage

```yaml
- uses: damoun/action-find-files@v2
  with:
    # The regex pattern to search filename for.
    pattern: '.*ya?ml$'
    # The path to search files in.
    path: '.'
```

## Exemple

```yaml
name: validate

on: [push, pull_request]

jobs:
  find_yaml_files:
    name: Find yaml files
    outputs:
      files: ${{ steps.find-files.outputs.files }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: damoun/action-find-files@v2
        id: find-files
        with:
          pattern: '.*ya?ml$'

  echo:
    name: Echo files
    needs: find_yaml_files
    strategy:
      matrix:
        file: ${{ fromJson(needs.find_yaml_files.outputs.files) }}
    runs-on: ubuntu-latest
    steps:
      - run: echo ${{ matrix.file }}
```