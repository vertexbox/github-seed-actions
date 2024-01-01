# RSS to Issue Action

A GitHub Action to creates GitHub issues from an RSS or Atom feed.

## Reference

<https://github.com/marketplace/actions/rss-to-issues>

## Example workflow

Step

```yaml
steps:
  uses: git-for-windows/rss-to-issues
  with:
    github-token: ${{ secrets.GITHUB_TOKEN }}
    feed: "https://cloud.google.com/feeds/kubernetes-engine-release-notes.xml"
```

Complete

```yaml
name: Monitor new upstream git release versions

on:
  workflow_dispatch:
  schedule:
    # Run this Action every day at 4:00pm UTC
    - cron: "0 16 * * *"

env:
  CHARACTER_LIMIT: 1000
  MAX_AGE: 7d

jobs:
  scrape:
    runs-on: ubuntu-latest
    permissions:
      issues: write
    strategy:
      matrix:
        include:
          - project: kubernetes
            labels: kubernetes
            feed: https://github.com/kubernetes/kubernetes/releases.atom
      fail-fast: false
    steps:
      - uses: git-for-windows/rss-to-issues@v0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          feed: ${{ matrix.feed }}
          prefix: "[New ${{ matrix.project }} version]"
          character-limit: ${{ env.CHARACTER_LIMIT }}
          dry-run: false
          max-age: ${{ env.MAX_AGE }}
          labels: github/release,automated-issue,${{ matrix.labels }}
```

Real usage: <https://github.com/git-for-windows/git/blob/main/.github/workflows/monitor-components.yml>

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
