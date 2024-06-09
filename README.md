# action-find-files

A Github Action to find files.

## Usage

```yaml
- uses: damoun/action-find-files@v1
  with:
    # The pattern to search filename for.
    # It supports all the globbing capabilities of find command line.
    pattern: '*.yaml'
    # The path to search files in.
    path: '.'
```
