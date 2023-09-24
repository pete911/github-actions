# github-actions
Reusable [workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) for GitHub actions. This
makes it easier to maintain GitHub actions across projects.

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

## docker-push

`pete911/github-actions/.github/workflows/docker-push.yml@main` build and push docker image to dockerhub, but only if
the push is for tag that is prefixed with `v`.

### inputs

| input      | default | description                                        |
|------------|---------|----------------------------------------------------|
| build-args | N/A     | docker build args (see --build-arg in docker docs) |

### secrets

| input              | default | description                 |
|--------------------|---------|-----------------------------|
| DOCKERHUB_USERNAME | N/A     | dockerhub registry username |
| DOCKERHUB_TOKEN    | N/A     | dockerhub registry token    |

## docker-scan

`pete911/github-actions/.github/workflows/docker-scan.yml@main` builds and scans docker image.

## go

`pete911/github-actions/.github/workflows/go.yml@main` runs unit tests, go vet and trivy scan.

### inputs

| input        | default | description |
|--------------|---------|-------------|
| go-version   | 1.21.0  | go version  |

## go-releaser

`pete911/github-actions/.github/workflows/go-releaser.yml@main` runs go releaser, but only if the push is for tag that
is prefixed with `v`.

### inputs

| input        | default | description |
|--------------|---------|-------------|
| go-version   | 1.21.0  | go version  |

### secrets

| input             | default | description                                   |
|-------------------|---------|-----------------------------------------------|
| PUBLIC_REPO_TOKEN | N/A     | public repo token, needed to push to brew tap |
