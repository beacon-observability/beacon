# Roadmap

This page records development directions. It does not represent supported capabilities or committed delivery dates. Concrete tasks, owners, and progress are maintained in the corresponding projects.

## Near Term: Maintain and Expand Beacon Java

- Beacon Java `1.1.0` is published as a complete Agent JAR with checksum, SPDX SBOM, provenance,
  licenses, notices, and build-provenance attestations. Its opt-in Security capability is embedded
  in the Agent and follows the shared
  [Beacon Security specification](https://github.com/beacon-observability/beacon-security-spec).
- Exercise the documented upstream synchronization process against a later official version and
  keep Beacon-specific enhancements and regression evidence controlled.
- Continue Profiling evaluation. Profiling remains experimental and is not implied by the released
  Security capability.
- Validate telemetry with an actual receiver and document the compatible scope.

Java preserves the imported repository history and maintains its implementation, CI, and releases
in the language repository. See the [Java project entry](languages.md#java) for the current release
and maintainer documentation.

## Near Term: Extend the Python Release

- Beacon Python `1.1.0` is published through the documented Trusted Publisher workflow. Its
  opt-in Security capability is embedded in the existing `beacon-otel` wheel, and public-artifact
  acceptance covers the disabled lifecycle, findings, and runtime SBOM through OpenTelemetry Logs.
  See the [Python project entry](languages.md#python) for the current release and validation record.
- Continue expanding the actually validated upstream matrix and document version-specific Security
  support and rollback boundaries in the language repository.

## Later: Develop Go

- Inventory existing implementations and select the upstream project, source or dependency maintenance model, and enhancement scope.
- Establish build, test, upstream-tracking, and release processes.
- Add language onboarding documentation and actual support status under the shared maintenance principles.

The complete-source downstream approach used by Java has also been adopted for Python and PHP Contrib, but Go does not need to reuse the same branch layout, packaging, or feature list. Languages may progress independently according to available resources and maturity, and each completes its own validation and release.

## Near Term: Maintain and Expand the Node.js Release

- Beacon Node.js `1.2.0` publishes the complete zero-code product package and matching profiler and
  Security packages. Its opt-in Security capability is embedded in the existing zero-code preload
  workflow, and public-artifact acceptance covers disabled-by-default behavior, findings, runtime
  SBOM through OpenTelemetry Logs, and local-output defaults. See the
  [Node.js project entry](languages.md#nodejs) for the current release evidence.
- Continue expanding the actually validated upstream matrix and document version-specific Security
  support and rollback boundaries in the language repository.

## Later: Complete PHP Validation and Release

- Complete-source downstream projects have been established separately for OpenTelemetry PHP Contrib and the native extension. Beacon PHP Instrumentation `0.1.0` is published, and component packages are tested against its fixed release commit. See the [PHP project entry](languages.md#php) for current development status.
- Validate the target PHP versions, extension versions, and initial component instrumentations, including an actual ingestion path.
- Finalize the Composer packages' official versioning, publishing permissions, and upgrade and rollback procedures. Add version-specific user documentation after the initial official release.

## As Real Needs Emerge

- Upstream update detection and synchronization assistance.
- Multi-language onboarding examples and a documentation site.
- Maintain the released Java, Python, and Node.js Security capabilities, with each implementation
  owned, validated, and released by its corresponding language repository.
- Validated guidance for service identity, context, Profiling, and security-data correlation.

The roadmap does not assume a unified runtime, lockstep cross-language releases, a remote-control platform, or a new installation and injection system. New work must address a concrete user or maintenance need.
