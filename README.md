# lint-pull-request-title

A composite action for linting pull request titles.

Titles must follow the [Conventional Commits](https://www.conventionalcommits.org) specification, such as `feat: Add an input` or `chore(ci): Bump actions/checkout`. A scope is optional.

## Usage

```yaml
name: Pre-release

on:
  pull_request:
    types:
      - opened
      - edited
      - synchronize

permissions:
  pull-requests: read

jobs:
  title:
    name: Semantic Title
    runs-on: ubuntu-24.04
    steps:
      - name: Lint Pull Request Title
        uses: craigsloggett/lint-pull-request-title@v1
```

Trigger on `pull_request` rather than `pull_request_target`. The action only reads the pull request, so the read-only token that `pull_request` grants to forks and Dependabot is enough.

### Inputs

| Input   | Required? | Default               | Description                                     |
| ------- | --------- | --------------------- | ----------------------------------------------- |
| `token` | `false`   | `${{ github.token }}` | The GitHub token used to read the pull request. |
