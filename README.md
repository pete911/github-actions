# github-actions
Reusable [workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) for GitHub actions.

## example

```yaml
name: pipeline

on: [push]

permissions:
  contents: write

jobs:
  go:
    uses: pete911/github-actions/.github/workflows/go.yaml@main
    secrets:
      PUBLIC_REPO_TOKEN: ${{ secrets.PUBLIC_REPO_TOKEN }}
```

## go

`pete911/github-actions/.github/workflows/go.yaml@main` runs unit tests, go vet and trivy scan. If the commit contains
tag with `v` prefix, it also runs go releaser.

### inputs

| input        | default | description |
|--------------|---------|-------------|
| go-version   | 1.19.4  | go version  |

### secrets

| input             | default | description                                   |
|-------------------|---------|-----------------------------------------------|
| PUBLIC_REPO_TOKEN | N/A     | public repo token, needed to push to brew tap |
