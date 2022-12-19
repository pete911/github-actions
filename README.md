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
    uses: pete911/github-actions/.github/workflows/go.yml@main
  go-release:
    needs:
      - go
    uses: pete911/github-actions/.github/workflows/go-releaser.yml@main
    secrets:
      PUBLIC_REPO_TOKEN: ${{ secrets.PUBLIC_REPO_TOKEN }}
```

## go

`pete911/github-actions/.github/workflows/go.yml@main` runs unit tests, go vet and trivy scan.

### inputs

| input        | default | description |
|--------------|---------|-------------|
| go-version   | 1.19.4  | go version  |

## go-releaser

`pete911/github-actions/.github/workflows/go-releaser.yml@main` Runs go releaser if the push is for tag that is
prefixed with `v`.

### secrets

| input             | default | description                                   |
|-------------------|---------|-----------------------------------------------|
| PUBLIC_REPO_TOKEN | N/A     | public repo token, needed to push to brew tap |
