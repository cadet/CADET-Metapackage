# Contributing

This repository maintains and publishes the **CADET platform metapackage**, named **CADET** on PyPi.
It does not contain CADET functionality itself. Contributions therefore mainly concern **version management, CI, and release coordination**.

## Scope and responsibilities

This repository:

* publishes a **metapackage only**
* does not build or modify CADET components
* defines which versions of CADET packages are installed together

The metapackage installs:

* `cadet-core` (explicit version)
* `cadet-process` (explicit version)
* `cadet-python` implicitly, as a dependency of `cadet-process`

The `cadet-python` version is therefore **not set explicitly** in this repository.

## Version control via `pyproject.toml`

`pyproject.toml` is the **authoritative source** for the versions exposed by the metapackage.

The dependency entries for `cadet-core` and `cadet-process` define exactly what users receive when installing the metapackage from PyPI.
All released combinations always consist of package versions that already exist on PyPI.

To publish a new metapackage version, the dependency versions in `pyproject.toml` **must be updated**.

No workflow input overrides this.

## CI workflows overview

The repository uses three GitHub Actions workflows with clearly separated roles.

### `test_compatibility.yml`

Purpose: validate CADET version combinations.

Behavior:

* If no inputs are provided, versions are read from `pyproject.toml`.
* If inputs are provided, they control which versions or refs are **tested in CI**.
* All resolved versions are compared against the toml expectations.
* Mismatches are reported as warnings to make version drift explicit.

This workflow is used both standalone and as part of the publish process.

### `publish.yml`

Purpose: build and publish the metapackage to PyPI.

Behavior:

* Invokes `test_compatibility.yml` first.
* Builds and publishes the metapackage defined by `pyproject.toml`.
* Triggers a post publish installation test via `test_pypi_install.yml`.

The published package **always reflects the dependency versions in `pyproject.toml`**, independent of workflow inputs.

### `test_pypi_install.yml`

Purpose: validate the published package from a user perspective.

Behavior:

* Installs the metapackage from PyPI.
* Detects the installed CADET component versions.
* Checks out the matching `cadet-process` test suite.
* Runs upstream tests against the installed binaries.

This workflow verifies that the released package works in a clean environment.

## Normal release procedure

A standard release follows this sequence:

1. Update `cadet-core` and `cadet-process` dependency versions in `pyproject.toml`.
2. Trigger the `publish` workflow.
3. Compatibility is checked against the declared versions.
4. The metapackage is published to PyPI.
5. The published package is validated via installation tests.

## Workflow inputs and non standard releases

The `publish` and `test_compatibility` workflows accept inputs for `cadet-core` versions and `cadet-process` git refs.

These inputs:

* **only affect which versions are tested in CI**
* **do not affect what is released**

What is released is always the dependency combination declared in `pyproject.toml`.

Providing refs that do not match the toml is **not recommended**, but may be necessary when:

* older CADET-Process tags fail CI due to changes in CI infrastructure or tooling
* the PyPI released versions are known to be valid despite CI failures

In such cases:

* CI emits warnings highlighting the mismatch
* responsibility for correctness lies with the publisher

## Guidelines for contributors

* Do not add runtime logic or imports to this repository.
* Do not pin `cadet-python` explicitly.
* Always update `pyproject.toml` before releasing a new metapackage version.
* Treat CI warnings about version mismatches as signals, not noise.
