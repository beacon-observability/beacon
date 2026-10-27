# Language and Browser Projects

This page is the authoritative index of Beacon runtime agents, tracing SDKs, and the Rumable browser RUM project. Implementation approaches, feature scopes, and release schedules may differ by language. Support for one Beacon language or its upstream project must not be inferred for another.

Before onboarding a new language, use the [New Language Onboarding and Initial Release Guide](language-onboarding.md) to determine its maintenance model and validation boundaries. Projects that have not been established do not receive placeholder repository or installation links here.

## Java

Beacon Java uses a downstream copy of the complete OpenTelemetry Java Instrumentation source,
preserves upstream history, and adds Beacon-specific enhancements in the corresponding modules.
The current official release is `1.3.2`. It publishes one complete Agent JAR together with its
SHA-256 checksum, SPDX SBOM, provenance, licenses, notices, and GitHub build-provenance
attestations.

Beacon Security is embedded in that complete Agent as an opt-in capability and is disabled by
default. Applications still use one `-javaagent`; there is no standalone Security JAR.
The same official `1.3.2` Agent JAR is also distributed through the public
`ghcr.io/beacon-observability/beacon-java:1.3.2` container image for Linux amd64 and arm64.
The image supplies the Agent for an initContainer or an application-image build; it does not
include a JVM or an application. Refer to the release and pinned guides for exact scope and use.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-java](https://github.com/beacon-observability/beacon-java) |
| Current release | [Beacon Java 1.3.2](https://github.com/beacon-observability/beacon-java/releases/tag/v1.3.2) |
| Container image | [Beacon Java 1.3.2 on GHCR](https://github.com/orgs/beacon-observability/packages/container/package/beacon-java) |
| Container installation | [Beacon Java 1.3.2 image guide](https://github.com/beacon-observability/beacon-java/blob/c5cbb47749b249108718492adf9156b4dc66594d/beacon/docker/javaagent/README.md) |
| Kubernetes initContainer example | [Beacon Java 1.3.2 Kubernetes example](https://github.com/beacon-observability/beacon-java/blob/c5cbb47749b249108718492adf9156b4dc66594d/extensions/security/examples/kubernetes/init-container.yaml) |
| Earlier Security configuration reference | [Beacon Java 1.1.0 usage guide](https://github.com/beacon-observability/beacon-java/blob/cc55c77be6247d4f0e3835639002415b683a220b/extensions/security/README.md) |
| Source provenance | [Beacon Java 1.3.2 upstream baseline](https://github.com/beacon-observability/beacon-java/blob/v1.3.2/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-java/blob/main/beacon/UPSTREAM.md) |
| Release maintenance | [Beacon Java release process](https://github.com/beacon-observability/beacon-java/blob/main/beacon/RELEASING.md) |

The container guide and Kubernetes example are pinned to the distribution change merged after
`v1.3.2`; the image preserves the original release JAR. The earlier Security reference is explicitly
versioned `1.1.0` and does not define `1.3.2` support. The language repository's release record remains
authoritative for exact scope and evidence. Links to `main` are maintainer references and may change
with ongoing development.

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
JavaScript Contrib source and history. The current official release is `1.3.0`; it publishes the
`@beacon-observability/nodejs` zero-code package and the matching
`@beacon-observability/profiler-nodejs` and `@beacon-observability/security-nodejs` packages. The
general zero-code workflow is validated on Node.js 18.19, 20, 22, and 24. Beacon Security requires
Node.js 22.22.3+ or 24.11.1+.

Beacon Security is included in the complete zero-code package as an opt-in capability. It pins the
shared v1 contract, exports findings and runtime SBOM through OpenTelemetry Logs, and keeps local
diagnostic output off by default. The Kubernetes example bakes the complete package into the
application image without a separate Security image, sidecar, or init container. Public-artifact
acceptance verified installation from npm, zero-code trace and profile export, the disabled
lifecycle, request-specific occurrence IDs and trace context, evidence sampling, runtime-SBOM export,
and the local-output default. Version 1.3.0 adds conservative attack-evidence analysis with explicit
uncertainty; actual OTLP delivery verifies ordinary, suspected, and ordinary SQL evidence for one
finding.

The release link is authoritative for published scope. Entries that track `main` remain maintainer
references and may change with ongoing development.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-nodejs](https://github.com/beacon-observability/beacon-nodejs) |
| Current release | [Beacon Node.js 1.3.0](https://github.com/beacon-observability/beacon-nodejs/releases/tag/v1.3.0) |
| Published packages | [`@beacon-observability/nodejs@1.3.0`](https://www.npmjs.com/package/@beacon-observability/nodejs/v/1.3.0), [`@beacon-observability/profiler-nodejs@1.3.0`](https://www.npmjs.com/package/@beacon-observability/profiler-nodejs/v/1.3.0), and [`@beacon-observability/security-nodejs@1.3.0`](https://www.npmjs.com/package/@beacon-observability/security-nodejs/v/1.3.0) |
| Installation and Security usage | [Beacon Node.js 1.3.0 usage guide](https://github.com/beacon-observability/beacon-nodejs/blob/v1.3.0/packages/nodejs/README.md) |
| Kubernetes Deployment example | [Beacon Node.js 1.3.0 Kubernetes example](https://github.com/beacon-observability/beacon-nodejs/blob/v1.3.0/packages/security-nodejs/examples/kubernetes/deployment.yaml) |
| Release validation | [Beacon Node.js 1.3.0 public-artifact acceptance](https://github.com/beacon-observability/beacon-nodejs/blob/bc58b9409bb0c6cd4c5f966cdf9a9e6ee64be5a7/beacon/validation/1.3.0.md) |
| Development guide | [Beacon Node.js development entry](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/RELEASING.md) |

## Python

Beacon Python maintains a standalone downstream copy of the complete OpenTelemetry Python Contrib
source and is not a GitHub fork. The current official release is `1.2.1`; it publishes the
`beacon-otel` main distribution and the optional `beacon-profiling` distribution from the official
`v0.65b0` Contrib and `v1.44.0` Core baseline. The release record and version-pinned validation
document define the published scope. The former `gtrace` distribution is not a Beacon release.

Beacon Security is embedded in the existing `beacon-otel` wheel and `beacon` command instead of
introducing a third distribution. It is opt-in, keeps local output off by default, pins the shared
v1 contract, supports the Security runtime on standard-GIL CPython 3.11–3.14, and includes
Kubernetes and Gunicorn guidance. Public-artifact acceptance verified the disabled lifecycle and
finding plus runtime-SBOM delivery through OpenTelemetry Logs. Version 1.2.1 fixes Security
request lifecycles, propagation and SQL analysis, and bounds Profiling collection, shutdown and
export overhead. Public-package acceptance verified ordinary, suspected, and ordinary SQL
requests at one finding, including trace correlation, evidence sampling and compatible pprof
uploads. The versioned record distinguishes local protocol acceptance from DataKit qualification.

The release link is authoritative for published scope. Entries that track `main` remain maintainer
references and may change with ongoing development.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-python](https://github.com/beacon-observability/beacon-python) |
| Current release | [Beacon Python 1.2.1](https://github.com/beacon-observability/beacon-python/releases/tag/v1.2.1) |
| Published packages | [`beacon-otel==1.2.1`](https://pypi.org/project/beacon-otel/1.2.1/) and [`beacon-profiling==1.2.1`](https://pypi.org/project/beacon-profiling/1.2.1/) |
| Installation and Security usage | [Beacon Python 1.2.1 usage guide](https://github.com/beacon-observability/beacon-python/blob/v1.2.1/beacon-otel/README.md) |
| Kubernetes Deployment example | [Beacon Python 1.2.1 Kubernetes example](https://github.com/beacon-observability/beacon-python/blob/v1.2.1/beacon-otel/examples/kubernetes/deployment.yaml) |
| Release validation | [Beacon Python 1.2.1 public-artifact acceptance](https://github.com/beacon-observability/beacon-python/blob/93df6e89a925493687c5bf6ddbf1076aee424394/beacon/validation/1.2.1.md) |
| Development guide | [Beacon Python development entry](https://github.com/beacon-observability/beacon-python/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-python/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-python/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-python/blob/main/beacon/RELEASING.md) |

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

## Ruby

Beacon Ruby maintains an independent downstream of the complete official OpenTelemetry Ruby
Contrib source and history, with the official Ruby Core API, SDK, and exporters used as
dependencies. The first official Beacon Ruby source release is **v1.0.0**, distributed through
a fixed tag and a verified source archive with provenance and SHA-256 checksums.

Release acceptance covers the shared instrumentation base, all three Net::HTTP semantic modes,
and a local Collector OTLP HTTP/protobuf trace path with service identity and parent/client span
correlation. The source installation guide includes verification and rollback instructions.
This release retains upstream gem identities and does not publish an installable Beacon gem,
a prebuilt agent, or a complete runtime support matrix. Other frameworks, runtimes, DataKit,
Metrics, Logs, Profiling, and Security remain outside its validated scope.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-ruby](https://github.com/beacon-observability/beacon-ruby) |
| Current source release | [Beacon Ruby v1.0.0](https://github.com/beacon-observability/beacon-ruby/releases/tag/v1.0.0) |
| Source installation and rollback | [Beacon Ruby v1.0.0 source guide](https://github.com/beacon-observability/beacon-ruby/blob/v1.0.0/beacon/INSTALLATION.md) |
| Release notes and scope | [Beacon Ruby v1.0.0 notes](https://github.com/beacon-observability/beacon-ruby/blob/v1.0.0/beacon/releases/1.0.0.md) |
| Component acceptance | [Versioned source acceptance](https://github.com/beacon-observability/beacon-ruby/blob/v1.0.0/beacon/validation/README.md) |
| Development guide | [Beacon Ruby development entry](https://github.com/beacon-observability/beacon-ruby/blob/main/beacon/README.md) |
| Source baseline and synchronization | [OpenTelemetry Ruby upstream maintenance](https://github.com/beacon-observability/beacon-ruby/blob/main/beacon/UPSTREAM.md) |
| Release maintenance | [Beacon Ruby source release process](https://github.com/beacon-observability/beacon-ruby/blob/main/beacon/RELEASING.md) |

The release and version-pinned guides define the published scope. Links to `main` are mutable
maintainer references. See the [Ruby roadmap](roadmap.md#near-term-extend-the-ruby-source-release)
for future work.

## Rust

### Fastrace

[fastrace](https://github.com/beacon-observability/fastrace) is the Rust tracing library in the Beacon family. It is based on [fast/fastrace](https://github.com/fast/fastrace) and maintained as an independent source snapshot with a pinned upstream baseline, without a GitHub fork relationship. Upstream crate identities, APIs, copyright notices, and the Apache-2.0 license are retained. Applications add the SDK and instrument their source code.

The first official Beacon source release is **v0.1.0**, distributed through a fixed Git tag and a verified source archive. It is a Rust SDK that applications integrate and instrument explicitly. Release acceptance covers a two-process trace through local DataKit OTLP/gRPC, with backend verification of service names, the 128-bit trace ID, span IDs, parent relationships, and final pre-exit span delivery. The release notes and versioned guide define exact validation and limitations; this release does not publish crates.io packages or a prebuilt agent executable.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/fastrace](https://github.com/beacon-observability/fastrace) |
| Current source release | [Fastrace v0.1.0](https://github.com/beacon-observability/fastrace/releases/tag/v0.1.0) |
| Installation, local DataKit, and rollback | [Fastrace v0.1.0 installation](https://github.com/beacon-observability/fastrace/blob/v0.1.0/docs/installation.md) |
| Documentation | [Fastrace v0.1.0 guides](https://github.com/beacon-observability/fastrace/blob/v0.1.0/docs/README.md) |
| Source baseline and synchronization | [Upstream maintenance](https://github.com/beacon-observability/fastrace/blob/main/beacon/UPSTREAM.md) |
| Acceptance procedure and baseline record | [Local DataKit OTLP/gRPC acceptance](https://github.com/beacon-observability/fastrace/blob/v0.1.0/docs/validation.md) |
| Release maintenance | [Source release process](https://github.com/beacon-observability/fastrace/blob/main/beacon/RELEASING.md) |

Installation and acceptance guides are pinned to the release tag; the release notes record artifact acceptance. Maintenance links track development on `main` and may change. A possible future `beacon-rust` project based on OpenTelemetry Rust is separate and has not been established; no repository or installation link is provided for it.

## Rumable browser RUM

Rumable keeps its own name, `rumable` command, TOML configuration, and independent release schedule. The current official release is **v0.1.9**. It injects the bundled Web SDK into HTML responses through Linux/Nginx or Windows/IIS without changing application source code. Browsers report directly to the configured RUM receiver; browser reporting is configured separately from server-side OTLP export.

GitHub Releases provides Linux and Windows archives, installers, manifests, SDK metadata, and SHA256 checksums. The English configuration page generates commands pinned to a specific GitHub Release, and installers verify the selected archive before installation. Platform requirements, recovery procedures, and optional server-side OpenTelemetry integration remain documented in the Rumable repository.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/rumable](https://github.com/beacon-observability/rumable) |
| Current release and downloads | [v0.1.9](https://github.com/beacon-observability/rumable/releases/tag/v0.1.9) |
| Beacon documentation | [Rumable browser RUM guide](https://beacon-observability.github.io/docs/rumable) |
| English configuration page | [Rumable v0.1.9 setup](https://beacon-observability.github.io/rumable/0.1.9/setup/index.html) |
| Installation and recovery | [Rumable v0.1.9 user guide](https://github.com/beacon-observability/rumable/blob/v0.1.9/USER-GUIDE.md) |
| Platform compatibility | [Rumable v0.1.9 compatibility](https://github.com/beacon-observability/rumable/blob/v0.1.9/docs/compatibility.md) |
| Optional server tracing | [Rumable v0.1.9 OTel guide](https://github.com/beacon-observability/rumable/blob/v0.1.9/docs/otel.md) |
| Release maintenance | [GitHub publication and retry guide](https://github.com/beacon-observability/rumable/blob/main/docs/github-release.md) |

The release and version-pinned guides define published scope. The release-maintenance link tracks the mutable `main` branch. Rumable does not imply a browser SDK capability or release in every server-side language agent.

## Maintaining Support Scope

After an official release, each language's versioned documentation must list its validated telemetry and enhancement capabilities, runtime environments, ingestion compatibility, known limitations, and upgrade and rollback procedures.

When a cross-language comparison is needed, this repository only summarizes capabilities backed by an explicit version and evidence link; it does not duplicate complete test matrices. DataKit integration must be tied to the versions and protocols actually validated. Source availability, a successful build, or upstream support is not sufficient on its own to claim Beacon support.
