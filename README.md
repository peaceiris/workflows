## Composite Run Steps GitHub Actions

A collection of composite run steps GitHub Actions.

> [Creating a composite action - GitHub Docs](https://docs.github.com/en/actions/creating-actions/creating-a-composite-action)



## Setup Docker Project

This composite action includes the following actions:

- Install docker compose v2
- Install docker buildx

Definition: [setup-docker/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-docker/action.yml)

### Install the Latest Version

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
      - uses: peaceiris/workflows/setup-docker@v0.20.1
      - run: docker compose version
      - run: docker buildx version
```

### Install a Specific Version

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
      - uses: peaceiris/workflows/setup-docker@v0.20.1
        with:
          compose-version: '2.4.1'
          buildx-version: '0.8.2'
      - run: docker compose version
      - run: docker buildx version
```



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
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-go@v0.20.1
        with:
          go-version: '1.18'

      - run: go version
      - run: mage -h
      - run: goreleaser -h
```



## Setup Node.js Project

This composite action includes the following actions:

- `actions/setup-node`
- `actions/cache`

Definition: [setup-node/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-node/action.yml)

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-node@v0.20.1
        with:
          node-version: '16.14.2'
          # node-version-file: '.nvmrc'

      - run: node -v
      - run: npm -v
```



## Setup Python Project

This composite action includes the following actions:

- `actions/setup-python`
- `actions/cache`

Definition: [setup-python/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-python/action.yml)

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-python@v0.20.1
        with:
          python-version: '3.10'

      - run: python3 -V
      - run: python3 -m pip -V
      - run: python3 -m pipenv --version
```



## Setup Rust Project

This composite action includes the following actions:

- `actions/cache`

Definition: [setup-rust/action.yml](https://github.com/peaceiris/workflows/blob/main/setup-rust/action.yml)

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-rust@v0.20.1
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
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-goreleaser@v0.20.1

      - run: goreleaser -h
      - run: goreleaser check
```

### Install a Specific Version

```yaml
- uses: peaceiris/workflows/setup-goreleaser@v0.20.1
  with:
    goreleaser-version: '1.8.1'
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
      - uses: actions/checkout@v3

      - uses: peaceiris/workflows/setup-mage@v0.20.1

      - run: mage -h
      - run: mage fmt
```

### Install a Specific Version

```yaml
- uses: peaceiris/workflows/setup-mage@v0.20.1
  with:
    mage-version: '1.10.0'
```



## Reusable hadolint workflow

```yaml
jobs:
  hadolint:
    uses: peaceiris/workflows/.github/workflows/hadolint.yml@v0.20.1
```



## Reusable actionlint workflow

```yaml
jobs:
  actionlint:
    uses: peaceiris/workflows/.github/workflows/actionlint.yml@v0.20.1
```



## Reusable pull-request merger workflow

```yaml
name: pull-request

on:
  issue_comment:
    types: [created, edited]

jobs:
  merger:
    uses: peaceiris/workflows/.github/workflows/merger.yml@v0.20.1
```
