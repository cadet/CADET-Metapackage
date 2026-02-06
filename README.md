[![PyPI version](https://img.shields.io/pypi/v/cadet.svg)](https://pypi.org/project/cadet/)
[![Python](https://img.shields.io/pypi/pyversions/cadet.svg)](https://pypi.org/project/cadet/)
[![License](https://img.shields.io/github/license/cadet/cadet)](LICENSE)
[![CADET version compatibility](https://github.com/cadet/CADET-Metapackage/actions/workflows/test_compatibility.yml/badge.svg)](https://github.com/cadet/CADET-Metapackage/actions/workflows/test_compatibility.yml)
[![Verify CADET Metapackage](https://github.com/cadet/CADET-Metapackage/actions/workflows/test_pypi_install.yml/badge.svg)](https://github.com/cadet/CADET-Metapackage/actions/workflows/test_pypi_install.yml)

# CADET Metapackage

This package is a **metapackage** for the CADET platform.

It does not provide any importable Python modules itself.
Its only purpose is to install a curated set of CADET Python packages.

## Default packages

Installing `cadet` will install the following packages:

* **CADET-Process**
  Process analysis, optimization, and design toolkit
  PyPI: [https://pypi.org/project/cadet-process/](https://pypi.org/project/cadet-process/)
  Repository: [https://github.com/cadet/CADET-Process](https://github.com/cadet/CADET-Process)

* **CADET-Python**
  Python interface for CADET
  Installed as a dependency of `cadet-process`
  PyPI: [https://pypi.org/project/cadet-python/](https://pypi.org/project/cadet-python/)
  Repository: [https://github.com/cadet/CADET-Python](https://github.com/cadet/CADET-Python)

## Installation

Install the CADET platform metapackage:

```
pip install cadet
```

## Optional dependencies

Install the CADET metapackage plus research data management support:

```
pip install "cadet[rdm]"
```

This additionally installs:

* **CADET-RDM**
  Research data management utilities
  PyPI: [https://pypi.org/project/cadet-rdm/](https://pypi.org/project/cadet-rdm/)
  Repository: [https://github.com/cadet/CADET-RDM](https://github.com/cadet/CADET-RDM)

## Full platform bundle

Install the full platform bundle (currently identical to `cadet[rdm]`):

```
pip install "cadet[all]"
```

The `all` extra exists as a stable entry point if additional optional components are added in the future.

## Important notes

* This is a **metapackage only**.
  There is no `cadet` Python module to import.

* **Do not depend on `cadet` in other Python packages.**
  If you are developing a library, depend directly on the specific CADET components you use, such as `cadet-process` or `cadet-python`.

* This metapackage installs `cadet-core` from PyPI as part of the curated CADET stack.
  Alternative installation channels (for example conda-forge) may also be used if desired.

## Documentation and support

General CADET documentation and project information can be found at:

* [https://www.cadet.github.io](https://www.cadet.github.io)
* [https://github.com/cadet](https://github.com/cadet)

## Contributing and releases

For maintainers and contributors, including details on version management, CI workflows, and the release process, see:

* [`CONTRIBUTING.md`](CONTRIBUTING.md)