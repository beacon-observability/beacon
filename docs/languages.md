# Language Projects

This page is the authoritative index of language projects. Implementation approaches, feature scopes, and release schedules may differ by language. Support for one Beacon language or its upstream project must not be inferred for another.

Before onboarding a new language, use the [New Language Onboarding and Initial Release Guide](language-onboarding.md) to determine its maintenance model and validation boundaries. Projects that have not been established do not receive placeholder repository or installation links here.

## Java

Beacon Java uses a downstream copy of the complete OpenTelemetry Java Instrumentation source, preserves upstream history, and adds Beacon-specific enhancements in the corresponding modules. The project is currently being prepared and has no official Beacon Java release.

The following development entry points are available on GitHub and track the `main` development branch. Their contents may change with the branch and do not constitute installation instructions or support commitments for an official release.

| Entry | Development URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-java](https://github.com/beacon-observability/beacon-java) |
| Development guide | [Beacon Java development entry](https://github.com/beacon-observability/beacon-java/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-java/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-java/blob/main/beacon/UPSTREAM.md) |
| Release development | [Release process and prerequisites](https://github.com/beacon-observability/beacon-java/blob/main/beacon/RELEASING.md) |

These links point to development documentation that changes with the development branch. They do not represent installation instructions or support commitments for a particular official release. After the initial release, this page will link to version-specific user documentation and the corresponding GitHub Release.

## .NET

Beacon .NET maintains a standalone downstream copy of the complete OpenTelemetry .NET Automatic Instrumentation source and is not a GitHub fork. The current official version is `0.1.4`, with Linux glibc/musl, Windows, macOS, and NuGet archives, as well as installation scripts, checksums, an SPDX SBOM, and build provenance. The DataKit ingestion path is not yet within the validated support scope. Refer to the release notes for exact capabilities and limitations.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-dotnet](https://github.com/beacon-observability/beacon-dotnet) |
| Development guide | [Beacon .NET development entry](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [Synchronization process](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/UPSTREAM.md) |
| Current release | [Beacon .NET 0.1.4](https://github.com/beacon-observability/beacon-dotnet/releases/tag/beacon-v0.1.4) |

## Go

Beacon Go is planned for `beacon-observability/beacon-go`. The project has not yet been established. Existing implementations must first be inventoried and a maintenance model selected, so no repository or installation link is provided.

## Node.js

Beacon Node.js maintains a standalone downstream copy of the complete official OpenTelemetry JavaScript Contrib source and history. The project was established from the latest official `main` commit available at that time, `31b2af9dd5fcc5f96949e5666f8f45b30b997722`, and adds an experimental private profiling workspace without renaming inherited upstream packages.

The profiling workspace compiles and its six unit tests pass locally on Node.js 24. The complete upstream matrix, declared runtime matrix, DataKit ingestion, and release-candidate artifacts have not been validated. Inherited GitHub Actions remain disabled pending review, and there is no official Beacon Node.js release or installation entry.

The following development entry points track the `main` development branch. Their contents may change with the branch and do not constitute installation instructions or support commitments for an official release.

| Entry | Development URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-nodejs](https://github.com/beacon-observability/beacon-nodejs) |
| Development guide | [Beacon Node.js development entry](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/RELEASING.md) |

## Python

Beacon Python maintains a standalone downstream copy of the complete OpenTelemetry Python Contrib source and is not a GitHub fork. The development project preserves Beacon-specific enhancements and their history from the former `gtrace` branch and incorporates the official `v0.65b0` release baseline; its Python Core development dependency is pinned to `v1.44.0`. The former `gtrace` distribution has been removed. The `beacon-otel` main package and optional `beacon-profiling` development package have been implemented. Local unit tests and clean-environment installation and startup smoke tests on Python 3.10–3.14 have passed. The complete upstream matrix, DataKit ingestion, and release-candidate artifacts have not yet been validated, so there is no official Beacon Python release or installation entry.

The following development entry points are available on GitHub and track the `main` development branch. Their contents may change with the branch and do not constitute installation instructions or support commitments for an official release.

| Entry | Development URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-python](https://github.com/beacon-observability/beacon-python) |
| Development guide | [Beacon Python development entry](https://github.com/beacon-observability/beacon-python/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-python/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-python/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-python/blob/main/beacon/RELEASING.md) |

The Git history of `beacon-python` preserves the provenance of existing Beacon-specific implementations. Former PyPI packages do not constitute a Beacon Python release. After the initial release, this page will link to version-specific installation instructions and the corresponding GitHub Release.

## PHP

Beacon PHP uses two standalone downstream repositories rather than GitHub forks. `beacon-php` preserves the complete OpenTelemetry PHP Contrib history and maintains component instrumentation and the Composer metapackage. `beacon-php-instrumentation` preserves the complete history of the official native extension and incorporates existing cross-platform build and artifact experience. The repositories are integration-tested against pinned releases, and manual instrumentation does not require the extension. Beacon PHP Instrumentation `0.1.0` is published with Linux and Windows binaries, a PECL-compatible source package, and SHA-256 checksums after passing representative Linux, macOS, and Windows matrices and PHPT tests. Composer packages have passed installation and diagnostic integration on PHP 8.2 and 8.4 against the released extension commit. The complete component matrix, real ingestion path, and Composer package publication have not yet been completed, so the full Beacon PHP distribution still has no official release or installation entry.

The following development entry points are available on the GitHub `main` branch. Their contents may change as development progresses and do not constitute installation instructions or support commitments for an official release.

| Entry | Development URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-php](https://github.com/beacon-observability/beacon-php) |
| Native extension repository | [beacon-observability/beacon-php-instrumentation](https://github.com/beacon-observability/beacon-php-instrumentation) |
| Native extension release | [Beacon PHP Instrumentation 0.1.0](https://github.com/beacon-observability/beacon-php-instrumentation/releases/tag/v0.1.0) |
| Development guide | [Beacon PHP development entry](https://github.com/beacon-observability/beacon-php/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-php/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-php/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-php/blob/main/beacon/RELEASING.md) |
| Extension development guide | [Beacon PHP Instrumentation development entry](https://github.com/beacon-observability/beacon-php-instrumentation/blob/main/beacon/README.md) |
| Extension provenance | [Extension upstream baseline](https://github.com/beacon-observability/beacon-php-instrumentation/blob/main/beacon/upstream.lock.json) |

After the initial release, this page will link to version-specific installation instructions and the corresponding GitHub Release.

## Maintaining Support Scope

After an official release, each language's versioned documentation must list its validated telemetry and enhancement capabilities, runtime environments, ingestion compatibility, known limitations, and upgrade and rollback procedures.

When a cross-language comparison is needed, this repository only summarizes capabilities backed by an explicit version and evidence link; it does not duplicate complete test matrices. DataKit integration must be tied to the versions and protocols actually validated. Source availability, a successful build, or upstream support is not sufficient on its own to claim Beacon support.
