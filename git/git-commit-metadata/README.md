# Git Commit Metadata Action

A GitHub Action to retrieve the metadata associated with the given git commit.

## Inputs

```yaml
inputs:
  repository:
    required: true
    type: string
  ref:
    required: true
    type: string
  fetch-depth:
    required: false
    type: string
    default: 0
```

## Outputs

```yaml
outputs:
  git_sha_long: ${{ steps.metadata.outputs.git_sha_long }}
  git_sha_short: ${{ steps.metadata.outputs.git_sha_short }}
  git_commit_msg: ${{ steps.metadata.outputs.git_commit_msg }}
```

## Example workflow

```yml
steps:
```

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
