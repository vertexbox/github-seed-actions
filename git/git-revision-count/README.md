# Git Revision Count Action

A GitHub Action for retrieve the total number of revision based on a given git ref.

## Inputs

```yaml
inputs:
  ref:
    type: string
    description: "git ref"
    default: HEAD
```

## Outputs

```yaml
outputs:
  count:
    description: "git revision count"
    value: ${{ steps.rev_count.outputs.count }}
```

Description: The number of revisions based on the given git ref

## Example workflow

```yml
steps:
  - uses: actions/checkout@master
    with:
    fetch-depth: 0

  - name: git-revision-count
    id: git_rev_count
    uses: vertexbox/github-seed-actions/git/git-revision-count@master
    with:
    ref: ${{ github.ref }}

  - name: git-revision-count
    run: |
      echo ${{ steps.git_rev_count.outputs.count }}
    shell: bash
```

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
