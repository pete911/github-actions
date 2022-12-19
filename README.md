# github-actions
Reusable [workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows) for GitHub actions.

## go

`pete911/github-actions/.github/workflows/go.yaml@main` runs unit tests, go vet and trivy scan. If the commit contains
tag with `v` prefix, it also runs go releaser.

### secrets

| input             | default | description                                   |
|-------------------|---------|-----------------------------------------------|
| PUBLIC_REPO_TOKEN | N/A     | public repo token, needed to push to brew tap |
