# GREN changelog action

Update changelog file using [Gren](https://github.com/github-tools/github-release-notes).

## Usage

Configure Gren using `.grenrc` in your repository and run this action in GitHub actions workflow:

```yaml
name: Release notes

on: [release]
  types: [published]

jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: lakto/gren-action@v2.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.GH_TOKEN }}
        with:
          options: '--generate --override --changelog-filename=RELEASE_NOTES.md'
```

In options you can add all [options from Gren](https://github-tools.github.io/github-release-notes/options.html) itself except of `--username`, `--repo` and `--token`. They are already part of the lakto/gren-changelog-action entrypoint script.
