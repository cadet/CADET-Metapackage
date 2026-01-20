# CADET Platform Metapackage

This package is a **metapackage** for the CADET platform.

It does not provide any importable Python modules itself.
Its only purpose is to install a curated set of CADET Python packages.

## Default packages

Installing `cadet` will install the following packages:

* **CADET-Python**
  Python interface for CADET
  PyPI: [https://pypi.org/project/cadet-python/](https://pypi.org/project/cadet-python/)
  Repository: [https://github.com/cadet/CADET-Python](https://github.com/cadet/CADET-Python)

* **CADET-Process**
  Process analysis, optimization, and design toolkit
  PyPI: [https://pypi.org/project/cadet-process/](https://pypi.org/project/cadet-process/)
  Repository: [https://github.com/cadet/CADET-Process](https://github.com/cadet/CADET-Process)

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
  If you are developing a library, depend directly on the specific CADET components you use, such as `cadet-python` or `cadet-process`.

* This package does **not** install CADET-Core.
  CADET-Core is distributed via conda-forge and must be installed separately, for example with:

```
conda install cadet
```

## Documentation and support

General CADET documentation and project information can be found at:

* [https://www.cadet.github.io](https://www.cadet.github.io)
* [https://github.com/cadet](https://github.com/cadet)