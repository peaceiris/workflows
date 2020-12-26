## Composite Run Steps GitHub Actions

A collection of composite run steps GitHub Actions.

> [Creating a composite run steps action - GitHub Docs](https://docs.github.com/en/free-pro-team@latest/actions/creating-actions/creating-a-composite-run-steps-action)



## Setup [goreleaser/goreleaser]

Install `goreleaser` to a GitHub Actions virtual environment.

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

Install `mage` to a GitHub Actions virtual environment.

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
