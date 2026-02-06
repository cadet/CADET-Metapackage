# Security Policy

## Scope

The CADET platform metapackage does not implement any network services, authentication mechanisms, or remote communication features.

It is a pure packaging and dependency coordination layer that installs already released CADET components from PyPI.

As such, there are currently **no known security vulnerabilities specific to this repository**.

## Reporting security issues

If you believe you have identified a security issue related to this metapackage (for example unintended dependency behavior or supply chain concerns), please report it responsibly by:

- Opening a private security advisory on GitHub, or
- Contacting the CADET maintainers via the main project channels listed at  
  https://www.cadet.github.io

Please do not open public issues for suspected security problems.

## Third-party dependencies

Security issues in CADET components (`cadet-core`, `cadet-process`, `cadet-python`, etc.) should be reported to their respective repositories.

This repository does not modify or patch those components.
