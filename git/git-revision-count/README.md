# Git Revision Count Action

A GitHub Action for retrieve the total number of revision based on a given git ref.

## Inputs

`ref`

Description: **(Required)** git ref

Default: `HEAD`

## Outputs

`count`

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
