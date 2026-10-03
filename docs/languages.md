# Language Projects

This page is the authoritative index of language projects. Implementation approaches, feature scopes, and release schedules may differ by language. Support for one Beacon language or its upstream project must not be inferred for another.

Before onboarding a new language, use the [New Language Onboarding and Initial Release Guide](language-onboarding.md) to determine its maintenance model and validation boundaries. Projects that have not been established do not receive placeholder repository or installation links here.

## Java

Beacon Java uses a downstream copy of the complete OpenTelemetry Java Instrumentation source,
preserves upstream history, and adds Beacon-specific enhancements in the corresponding modules.
The current official release is `1.1.0`. It publishes one complete Agent JAR together with its
SHA-256 checksum, SPDX SBOM, provenance, licenses, notices, and GitHub build-provenance
attestations.

Beacon Security is embedded in that complete Agent as an opt-in capability and is disabled by
default. Applications still use one `-javaagent`; this release does not publish a standalone
Security JAR or a Beacon-owned container image. Refer to the release and pinned usage guide for
the exact configuration, capabilities, deployment example, and limitations.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-java](https://github.com/beacon-observability/beacon-java) |
| Current release | [Beacon Java 1.1.0](https://github.com/beacon-observability/beacon-java/releases/tag/v1.1.0) |
| Installation and Security usage | [Beacon Java 1.1.0 usage guide](https://github.com/beacon-observability/beacon-java/blob/cc55c77be6247d4f0e3835639002415b683a220b/extensions/security/README.md) |
| Kubernetes initContainer example | [Beacon Java 1.1.0 Kubernetes example](https://github.com/beacon-observability/beacon-java/blob/cc55c77be6247d4f0e3835639002415b683a220b/extensions/security/examples/kubernetes/init-container.yaml) |
| Source provenance | [Beacon Java 1.1.0 upstream baseline](https://github.com/beacon-observability/beacon-java/blob/v1.1.0/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-java/blob/main/beacon/UPSTREAM.md) |
| Release maintenance | [Beacon Java release process](https://github.com/beacon-observability/beacon-java/blob/main/beacon/RELEASING.md) |

The usage guide is pinned to a documentation-only correction merged after `v1.1.0`; it does not
change or replace the immutable release artifacts. The language repository's release record remains
authoritative for exact scope and evidence. Links to `main` are maintainer references and may
change with ongoing development.

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

Beacon Node.js maintains a standalone downstream copy of the complete official OpenTelemetry
JavaScript Contrib source and history. The current official release is `1.1.0`; it publishes the
`@beacon-observability/nodejs` zero-code package and the matching
`@beacon-observability/profiler-nodejs` package. It supports the documented preload workflow on
Node.js 18.19, 20, 22, and 24. Its release record contains the exact build commits, npm package
digests, CI evidence, and verified telemetry scope.

Beacon Security is not part of `1.1.0`. The open implementation PR embeds it behind the existing
zero-code package as an opt-in capability, pins the shared v1 contract, keeps local output off by
default, and adds a Kubernetes example without a separate Security image, sidecar, or init
container. This source work and its CI results are development evidence, not a published Security
capability or support commitment.

The release link is authoritative for published scope. Entries that track `main` remain maintainer
references and may change with ongoing development.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-nodejs](https://github.com/beacon-observability/beacon-nodejs) |
| Current release | [Beacon Node.js 1.1.0](https://github.com/beacon-observability/beacon-nodejs/releases/tag/beacon-v1.1.0) |
| Published package | [`@beacon-observability/nodejs@1.1.0`](https://www.npmjs.com/package/@beacon-observability/nodejs/v/1.1.0) |
| Development guide | [Beacon Node.js development entry](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/RELEASING.md) |
| Security implementation status | [Beacon Node.js PR #2](https://github.com/beacon-observability/beacon-nodejs/pull/2) |

## Python

Beacon Python maintains a standalone downstream copy of the complete OpenTelemetry Python Contrib
source and is not a GitHub fork. The current official release is `1.0.1`; it publishes the
`beacon-otel` main distribution and the optional `beacon-profiling` distribution from the official
`v0.65b0` Contrib and `v1.44.0` Core baseline. The release record and version-pinned validation
document define the published scope. The former `gtrace` distribution is not a Beacon release.

Beacon Security is not part of `1.0.1`. The open implementation PR embeds it in the existing
`beacon-otel` wheel and `beacon` command instead of introducing a third distribution. It is opt-in,
keeps local output off by default, pins the shared v1 contract, supports the Security runtime on
standard-GIL CPython 3.11–3.14, and includes Kubernetes and Gunicorn guidance. This source work and
its CI results are development evidence, not a published Security capability or support
commitment.

The release link is authoritative for published scope. Entries that track `main` remain maintainer
references and may change with ongoing development.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-python](https://github.com/beacon-observability/beacon-python) |
| Current release | [Beacon Python 1.0.1](https://github.com/beacon-observability/beacon-python/releases/tag/v1.0.1) |
| Published package | [`beacon-otel==1.0.1`](https://pypi.org/project/beacon-otel/1.0.1/) |
| Release validation | [Beacon Python 1.0.1 acceptance record](https://github.com/beacon-observability/beacon-python/blob/v1.0.1/beacon/validation/1.0.1.md) |
| Development guide | [Beacon Python development entry](https://github.com/beacon-observability/beacon-python/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-python/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-python/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-python/blob/main/beacon/RELEASING.md) |
| Security implementation status | [Beacon Python PR #15](https://github.com/beacon-observability/beacon-python/pull/15) |

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
