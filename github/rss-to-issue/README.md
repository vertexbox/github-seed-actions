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
  kubernetes-release:
    runs-on: ubuntu-latest
    steps:
      - uses: git-for-windows/rss-to-issues@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          feed: https://github.com/kubernetes/kubernetes/tags.atom
          prefix: "[Git]"
          character-limit: 255
          dry-run: false
          max-age: 48h
          labels: git
```

## License

All composite actions and unit tests in this project are released under the [MIT License](../../LICENSE)
