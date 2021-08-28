## Composite Run Steps GitHub Actions

A collection of composite run steps GitHub Actions.

> [Creating a composite run steps action - GitHub Docs](https://docs.github.com/en/free-pro-team@latest/actions/creating-actions/creating-a-composite-run-steps-action)



## Setup Go Project

This composite action includes the following actions:

- `actions/setup-go`
- `peaceiris/workflows/setup-mage`
- `peaceiris/workflows/setup-goreleaser`
- `actions/cache`

Definition: [setup-go/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-go/action.yml)

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2

      - uses: peaceiris/workflows/setup-go@v0.9.0
        with:
          go-version: '1.17'

      - run: go version
      - run: mage -h
      - run: goreleaser -h
```



## Setup [goreleaser/goreleaser]

Install `goreleaser` to a GitHub Actions Ubuntu virtual environment.

Definition: [setup-goreleaser/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-goreleaser/action.yml)

[goreleaser/goreleaser]: https://github.com/goreleaser/goreleaser/

### Install the Latest Version

Here is an example GitHub Actions workflow to install the latest `goreleaser` and run it.

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2

      - uses: peaceiris/workflows/setup-goreleaser@v0.8.1

      - run: goreleaser -h
      - run: goreleaser check
```

### Install a Specific Version

```yaml
- uses: peaceiris/workflows/setup-goreleaser@v0.8.1
  with:
    goreleaser-version: '0.149.0'
```



## Setup [magefile/mage]

Install `mage` to a GitHub Actions Ubuntu virtual environment.

Definition: [setup-mage/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-mage/action.yml)

[magefile/mage]: https://github.com/magefile/mage

### Install the Latest Version

Here is an example GitHub Actions workflow to install the latest `mage` and run it.

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-18.04
    steps:
      - uses: actions/checkout@v2

      - uses: peaceiris/workflows/setup-mage@v0.8.1

      - run: mage -h
      - run: mage fmt
```

### Install a Specific Version

```yaml
- uses: peaceiris/workflows/setup-mage@v0.8.1
  with:
    mage-version: '1.10.0'
```
