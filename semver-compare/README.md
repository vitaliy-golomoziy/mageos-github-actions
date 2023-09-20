# "Semver Compare" Action

A Github Action that semantically compares two versions, like 2.1.1 and 2.3.0. Returns -1 if first version is lower, 0 if they are equal and 1 otherwise

## Inputs

See the [action.yml](./action.yml)

## Usage

```yml
name: Semver Compare

on:
  push:
    branches:
    - main
  pull_request:
    branches:
    - main

jobs:
  version:
    runs-on: ubuntu-latest
    name: A job to semantically compare two versions
    steps:
      - uses: actions/checkout@v3
      - uses: mage-os/github-actions/semver-compare@main
        id: semver-compare
        with:
            version: 2.1.0
            compare_against: 2.2.3
      - run: echo version ${{ steps.semver-compare.outputs.result }}
        shell: bash
```
