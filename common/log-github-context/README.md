# Dump Contexts To Log Action

A GitHub Action to dump relevant workflow context metadata to console log.

## References

<https://docs.github.com/en/actions/learn-github-actions/contexts>

## Example workflow

```yml
steps:
  - name: log-github-context
    uses: vertexbox/github-seed-actions/common/log-github-context@master
```

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
