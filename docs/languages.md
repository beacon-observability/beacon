# Language, eBPF, and Browser Projects

This page is the authoritative index of Beacon runtime agents, tracing SDKs, the OBI eBPF instrumentation project, and the Rumable browser RUM project. Implementation approaches, feature scopes, and release schedules may differ by component. Support for one Beacon component or its upstream project must not be inferred for another.

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

Beacon .NET 2.0.1 maintains a standalone downstream of OpenTelemetry .NET Automatic
Instrumentation. It distributes Linux glibc/musl, Windows, macOS and NuGet archives,
DEB/RPM/MSI installers, checksums, an SPDX SBOM and GitHub artifact attestations.
Security remains experimental and opt-in. Its compact schema-v2 LogRecord Body
moves event time and occurrence identity to native OTel metadata; upgrade consumers
before upgrading. Runtime-specific Security acceptance is narrower than the archive
platform set. The release record defines platform and installer lifecycle validation;
DataKit/backend ingestion is outside that acceptance.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-dotnet](https://github.com/beacon-observability/beacon-dotnet) |
| Current release and acceptance | [Beacon .NET v2.0.1](https://github.com/beacon-observability/beacon-dotnet/releases/tag/v2.0.1) |
| Installation and rollback | [Versioned launcher guide](https://github.com/beacon-observability/beacon-dotnet/blob/v2.0.1/beacon/README.md) |
| Security and contract provenance | [Versioned Security reference](https://github.com/beacon-observability/beacon-dotnet/tree/v2.0.1/beacon/security) |
| Development guide | [Mutable development entry](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/README.md) |
| Source provenance | [Released upstream baseline](https://github.com/beacon-observability/beacon-dotnet/blob/v2.0.1/beacon/upstream.lock.json) |
| Upstream maintenance | [Synchronization process](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/UPSTREAM.md) |

## C++

Beacon C++ maintains an independent downstream of the complete official OpenTelemetry C++
API, SDK, and exporters, preserving upstream source history and license notices. The first
Beacon source release is **v0.1.0**, distributed as a fixed tag and verified source archive
with pinned protocol sources, SHA-256 checksums, and provenance. Applications explicitly
initialize the SDK and instrument their source code; upstream CMake identities and namespaces
remain unchanged.

Release acceptance covers Linux x86_64, Debian 13, GCC 14.2.0, C++17 standard-library mode,
ABI v1, static SDK installation and consumption, and OTLP/HTTP Protobuf traces to Collector
Contrib 0.135.0. The receiver verifier checks service identity, exact trace/span IDs, parent
relationships, and final delivery during shutdown. This does not establish DataKit or downstream
backend compatibility. Metrics, Logs, other platforms and protocols, Profiling, Beacon Security,
and automatic instrumentation remain outside first-release acceptance. No prebuilt agent,
binary package, or package-index distribution is published.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-cpp](https://github.com/beacon-observability/beacon-cpp) |
| Current release | [Beacon C++ v0.1.0](https://github.com/beacon-observability/beacon-cpp/releases/tag/v0.1.0) |
| Installation and rollback | [Versioned source installation guide](https://github.com/beacon-observability/beacon-cpp/blob/v0.1.0/beacon/INSTALL.md) |
| Trace integration and verification | [Versioned acceptance guide](https://github.com/beacon-observability/beacon-cpp/blob/v0.1.0/beacon/acceptance/README.md) |
| Validation scope | [Versioned validation record](https://github.com/beacon-observability/beacon-cpp/blob/v0.1.0/beacon/VALIDATION.md) |
| Development guide | [Beacon C++ development entry](https://github.com/beacon-observability/beacon-cpp/blob/main/beacon/README.md) |
| Source provenance and upstream maintenance | [Baseline and synchronization process](https://github.com/beacon-observability/beacon-cpp/blob/main/beacon/UPSTREAM.md) |
| Release maintenance | [Release process](https://github.com/beacon-observability/beacon-cpp/blob/main/beacon/RELEASING.md) |

Installation and acceptance links are pinned to the release tag. Links to `main` are mutable
maintainer references; the release notes and attached manifest define exact artifact acceptance.

## Go

Beacon Go is planned for `beacon-observability/beacon-go`. The project has not yet been established. Existing implementations must first be inventoried and a maintenance model selected, so no repository or installation link is provided.

## Node.js

Beacon Node.js maintains a standalone downstream copy of the complete official OpenTelemetry
JavaScript Contrib source and history. The current official release is `4.0.0`; it publishes the
`@beacon-observability/nodejs` zero-code package and the matching
`@beacon-observability/profiler-nodejs` and `@beacon-observability/security-nodejs` packages. The
general zero-code workflow is validated on Node.js 18.19, 20, 22, and 24. Beacon Security requires
Node.js 22.22.3+ or 24.11.1+.

Beacon Security is included in the complete zero-code package as an opt-in capability. It pins the
compact schema-v2 LogRecord Body contract, with native OTel event time and
`attributes.event_id`; consumers parse Body once without a SIEM `message` wrapper.
Fingerprint v1 and inventory IDs are unchanged. Local Body-only diagnostics omit
native time and identity. Security remains opt-in with default no-evidence filtering.
Public npm artifacts, zero-code trace/profile export and ESM Security preload passed
acceptance. The Release retains exact package manifests and checksum receipts.

The public `ghcr.io/beacon-observability/beacon-nodejs:4.0.0` image supplies the same
published packages for Linux amd64 and arm64. Both native candidates passed; anonymous
pull and Kubernetes initContainer injection passed on Linux amd64, with a read-only
non-root application and actual traces, native profiles and Security SBOM. The image
runtime/native-library boundary is narrower than the npm matrix; use its pinned guide.

The release link is authoritative for published scope. Entries that track `main` remain maintainer
references and may change with ongoing development.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-nodejs](https://github.com/beacon-observability/beacon-nodejs) |
| Current release | [Beacon Node.js 4.0.0](https://github.com/beacon-observability/beacon-nodejs/releases/tag/v4.0.0) |
| Published packages | [`@beacon-observability/nodejs@4.0.0`](https://www.npmjs.com/package/@beacon-observability/nodejs/v/4.0.0), [`@beacon-observability/profiler-nodejs@4.0.0`](https://www.npmjs.com/package/@beacon-observability/profiler-nodejs/v/4.0.0), and [`@beacon-observability/security-nodejs@4.0.0`](https://www.npmjs.com/package/@beacon-observability/security-nodejs/v/4.0.0) |
| Installation and Security usage | [Beacon Node.js 4.0.0 usage guide](https://github.com/beacon-observability/beacon-nodejs/blob/v4.0.0/packages/nodejs/README.md) |
| Container image | [Beacon Node.js 4.0.0 on GHCR](https://github.com/orgs/beacon-observability/packages/container/package/beacon-nodejs) |
| Container installation | [Beacon Node.js 4.0.0 image guide](https://github.com/beacon-observability/beacon-nodejs/blob/v4.0.0/beacon/docker/nodejs/README.md) |
| Container Kubernetes example | [Beacon Node.js 4.0.0 initContainer](https://github.com/beacon-observability/beacon-nodejs/blob/v4.0.0/beacon/docker/nodejs/init-container.yaml) |
| Kubernetes Deployment example | [Beacon Node.js 4.0.0 Kubernetes example](https://github.com/beacon-observability/beacon-nodejs/blob/v4.0.0/packages/security-nodejs/examples/kubernetes/deployment.yaml) |
| Release validation | [Beacon Node.js 4.0.0 public-artifact acceptance](https://github.com/beacon-observability/beacon-nodejs/releases/tag/v4.0.0) |
| Development guide | [Beacon Node.js development entry](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/README.md) |
| Source provenance | [Upstream baseline record](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-nodejs/blob/main/beacon/RELEASING.md) |

## Python

Beacon Python maintains a standalone downstream copy of the complete OpenTelemetry Python Contrib
source and is not a GitHub fork. The current official release is `1.4.0`, publishing matching
`beacon-otel` and optional `beacon-profiling` distributions. The versioned release notes and source
provenance records in the language repository define its Contrib `v0.66b2` / Core `v1.45.2` baseline and published scope.
The former `gtrace` distribution is not a Beacon release.

Beacon Security remains embedded in `beacon-otel`, opt-in and disabled by default, with local
output off. Release 1.4.0 exports compact v2 JSON directly as the OTel Logs Body.
Event time moves to native `time_unix_nano`; finding occurrence identity moves to LogRecord
`attributes.event_id`. Body omits `observed_at` and `occurrence_id`; remaining evidence,
dependencies, and correlation keep their v2 paths. Consumers must coordinate this migration;
historical 1.3.0 SIEM records retain their original decoder. Diagnostic JSONL retains native
metadata outside its `body` string. Fingerprint v1 is unchanged. Security supports standard-GIL
CPython 3.11–3.14.

Individual instrumentation extras and `[all]` cover 51 plugins, while profiling remains a separate
extra. The protected release workflow built and tested both distributions before publication.
Public-index checks on CPython 3.14.3 verified base, selected, all, and all-plus-profiling installs,
dependency consistency, zero-code startup, and no default local files. The four GitHub Release
assets match their PyPI SHA-256 digests. Candidate wheels passed 20 package, 281 Security,
and 116 Profiling tests, plus five package subtests. A real Flask request reached a local
Collector with finding, inventory, and Trace data under the native log binding. These checks
do not establish production-backend acceptance.
Profiling retains the multipart pprof `http` exporter and the `file` exporter; follow the versioned
migration notes for the changes from the 1.2.6 OTLP configuration.

| Item | Entry point |
| --- | --- |
| Source repository | [beacon-observability/beacon-python](https://github.com/beacon-observability/beacon-python) |
| Current release | [Beacon Python 1.4.0](https://github.com/beacon-observability/beacon-python/releases/tag/v1.4.0) |
| Published packages | [`beacon-otel==1.4.0`](https://pypi.org/project/beacon-otel/1.4.0/) and [`beacon-profiling==1.4.0`](https://pypi.org/project/beacon-profiling/1.4.0/) |
| Installation and Security usage | [Beacon Python 1.4.0 usage guide](https://github.com/beacon-observability/beacon-python/blob/v1.4.0/beacon-otel/README.md) |
| Kubernetes Deployment example | [Beacon Python 1.4.0 Kubernetes example](https://github.com/beacon-observability/beacon-python/blob/v1.4.0/beacon-otel/examples/kubernetes/deployment.yaml) |
| Release validation | [Beacon Python 1.4.0 build, tests and publication](https://github.com/beacon-observability/beacon-python/actions/runs/45799030738) |
| Earlier Security verification | [Beacon Python 1.2.3 public-artifact verification](https://github.com/beacon-observability/beacon-python/blob/08dcc4f31f50b7610435b88f23d9cd4b1353e9b1/beacon/validation/1.2.3.md) |
| Development guide | [Beacon Python development entry](https://github.com/beacon-observability/beacon-python/blob/main/beacon/README.md) |
| Source provenance | [Release source baseline](https://github.com/beacon-observability/beacon-python/blob/v1.4.0/beacon/upstream.lock.json) |
| Upstream maintenance | [OpenTelemetry synchronization process](https://github.com/beacon-observability/beacon-python/blob/main/beacon/UPSTREAM.md) |
| Release preparation | [Release prerequisites](https://github.com/beacon-observability/beacon-python/blob/main/beacon/RELEASING.md) |

## PHP

Beacon PHP **3.0.0** is a lightweight Agent and isolated zero-code distribution,
with selected official Composer instrumentation rather than a vendored Contrib
source tree. Its installer selects the independently released Beacon native
extension **1.1.0** (OpenTelemetry module 1.5.0). The declared standalone scope is
Linux glibc x86_64 and PHP 8.2–8.4; match native PHP/architecture/ABI variants exactly.
GitHub assets include the compiled setup script, isolated runtime, Composer library
ZIP, license and SHA-256 checksums. Packagist publication is not claimed.

Experimental Security remains opt-in. Version 3.0.0 uses compact single-line schema-v2
JSON in LogRecord Body, native OTel event time and `attributes.event_id`, without a
SIEM envelope or `message` wrapper. Fingerprint v1 and inventory IDs are unchanged;
upgrade consumers first. Default no-evidence filtering remains. Its PHP inventory lifecycle remains synchronous/cooperative: idle
processes have no independent scheduler, and long-running multi-request frameworks
lack a request-reset adapter. Refer to the versioned Security guide for these gaps.
Collector receipt and cold-install acceptance do not establish production backend
storage or every application/framework combination.

| Entry | URL |
| --- | --- |
| Current Agent release | [Beacon PHP 3.0.0](https://github.com/beacon-observability/beacon-php/releases/tag/v3.0.0) |
| Zero-code installation and rollback | [Beacon PHP 3.0.0 standalone guide](https://github.com/beacon-observability/beacon-php/blob/v3.0.0/docs/standalone.md) |
| Security migration and limits | [Beacon PHP 3.0.0 Security](https://github.com/beacon-observability/beacon-php/releases/tag/v3.0.0) |
| Source repository | [beacon-observability/beacon-php](https://github.com/beacon-observability/beacon-php) |
| Native extension release | [Beacon PHP Instrumentation 1.1.0](https://github.com/beacon-observability/beacon-php-instrumentation/releases/tag/v1.1.0) |
| Native installation | [Versioned native guide](https://github.com/beacon-observability/beacon-php-instrumentation/blob/v1.1.0/beacon/README.md) |
| Agent provenance | [Released compatibility lock](https://github.com/beacon-observability/beacon-php/blob/v3.0.0/beacon/compatibility.lock.json) |
| Development guide | [Mutable Beacon PHP maintenance entry](https://github.com/beacon-observability/beacon-php/blob/main/beacon/README.md) |

## Ruby

Beacon Ruby maintains an independent downstream of the complete official OpenTelemetry Ruby
Contrib source and history, with the official Ruby Core API, SDK, and exporters used as
dependencies. The current source release is **v2.0.0**, distributed through a fixed tag,
a verified source archive, provenance and SHA-256 checksums. It also distributes the
independently versioned Security 0.3.0 and experimental profiling 0.1.1 gems on GitHub,
not RubyGems.

The source trace path covers the shared instrumentation base, Net::HTTP semantic modes
and local Collector OTLP HTTP/protobuf trace delivery. Opt-in Security findings and runtime
inventories use the host Logs SDK. Security 0.3.0 exports compact schema-v2 JSON directly in LogRecord Body,
with native OTel event time and `attributes.event_id`. Body-only diagnostics omit
those native values. There is no SIEM `message` wrapper; fingerprint v1 and inventory
IDs are unchanged. Source and separately installed gem Collector acceptance passed;
default no-evidence filtering remains, and consumers must migrate before upgrading.
Experimental profiling adds CPU/wall time, allocation
counts, sampled live heap objects/bytes and GVL waits, with local DataKit pprof upload.
Profiling compile/test/build CI passes Linux CRuby 3.3, 3.4 and 4.0; local receiver
acceptance uses 3.3.12. Source availability is not a complete runtime or production
overhead guarantee. See the versioned guides for explicit setup, limits and rollback.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-ruby](https://github.com/beacon-observability/beacon-ruby) |
| Current source release | [Beacon Ruby v2.0.0](https://github.com/beacon-observability/beacon-ruby/releases/tag/v2.0.0) |
| Source installation and rollback | [Beacon Ruby v2.0.0 source guide](https://github.com/beacon-observability/beacon-ruby/blob/v2.0.0/beacon/INSTALLATION.md) |
| Release notes and scope | [Beacon Ruby v2.0.0 notes](https://github.com/beacon-observability/beacon-ruby/blob/v2.0.0/beacon/releases/2.0.0.md) |
| Component acceptance | [Published artifact and receiver acceptance](https://github.com/beacon-observability/beacon-ruby/releases/tag/v2.0.0) |
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

## OBI eBPF instrumentation

OpenTelemetry eBPF Instrumentation (OBI) provides eBPF-based, zero-code instrumentation
for user-space applications. It is a separate instrumentation approach from a language SDK
or runtime agent; adding OBI here does not establish a Beacon Go agent.

[Beacon OBI](https://github.com/beacon-observability/beacon-obi) maintains an independent
complete-source downstream of official OpenTelemetry eBPF Instrumentation `v1.0.0`, preserving
upstream history and licensing without a GitHub fork relationship. The first Beacon release,
**0.1.0**, provides a standalone Linux amd64 executable, checksums, a CycloneDX component
inventory, and local build provenance. The upstream baseline and Beacon version are independent.

Acceptance covers HTTP/1 server spans, service identity, trace/span identifiers, request-duration
metrics, and clean shutdown through a local OTLP HTTP/protobuf receiver on Ubuntu 24.04,
kernel 6.11, and CPython 3.14.3. It does not establish other platform/runtime matrices, DataKit
or production-backend compatibility, Kubernetes deployment, Profiling, or Security support.
No Beacon container image or Collector receiver module is released.

| Entry | URL |
| --- | --- |
| Source repository | [beacon-observability/beacon-obi](https://github.com/beacon-observability/beacon-obi) |
| Current release and acceptance | [Beacon OBI 0.1.0](https://github.com/beacon-observability/beacon-obi/releases/tag/v0.1.0) |
| Installation and rollback | [Beacon OBI 0.1.0 guide](https://github.com/beacon-observability/beacon-obi/blob/v0.1.0/beacon/INSTALLATION.md) |
| Source baseline | [OBI 0.1.0 upstream record](https://github.com/beacon-observability/beacon-obi/blob/v0.1.0/beacon/UPSTREAM.md) |
| Development guide | [Beacon OBI development entry](https://github.com/beacon-observability/beacon-obi/blob/main/beacon/README.md) |
| Release maintenance | [Beacon OBI release process](https://github.com/beacon-observability/beacon-obi/blob/main/beacon/RELEASING.md) |

The release and versioned guide define published scope. Development and maintenance links
track mutable `main` branches. See the [OBI roadmap](roadmap.md#later-validate-obi-ebpf-instrumentation)
for remaining validation work. OBI is separate from the planned Go language agent.

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
