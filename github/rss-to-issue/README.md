# RSS to Issue Action

A GitHub Action to creates GitHub issues from an RSS or Atom feed.

## Reference

<https://github.com/marketplace/actions/rss-to-issues>

## Example workflow

Step

```yml
steps:
  uses: git-for-windows/rss-to-issues
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    feed: "https://cloud.google.com/feeds/kubernetes-engine-release-notes.xml"
```

Complete

```yml
name: Monitor new Git versions

on:
  schedule:
    # Run this Action every day at 7:37am UTC
    - cron: "37 7 * * *"

jobs:
  monitor-git-release:
    runs-on: ubuntu-latest
    permissions:
      issues: write
    strategy:
      matrix:
        include:
          - project: kubernetes
            labels: kubernetes/kubernetes
            feed: https://github.com/kubernetes/kubernetes/releases.atom
      fail-fast: false
    steps:
      - uses: git-for-windows/rss-to-issues@v0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          feed: ${{ matrix.feed }}
          prefix: "[New ${{ matrix.project }} version]"
          character-limit: 255
          dry-run: false
          max-age: 30d
          labels: github/release,automated-issue,${{ matrix.labels }}
```

Real usage: <https://github.com/git-for-windows/git/blob/main/.github/workflows/monitor-components.yml>

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
