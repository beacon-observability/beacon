# Roadmap

This page records development directions. It does not represent supported capabilities or committed delivery dates. Concrete tasks, owners, and progress are maintained in the corresponding projects.

## Near Term: Complete the Java Development and Release Cycle

- Inventory the imported downstream changes and identify the enhancements and tests to retain.
- Build from pinned source, validate runtime behavior, and rehearse one official-version synchronization.
- Establish Beacon Java versioning, artifacts, release notes, and upgrade and rollback procedures.
- Evaluate and validate Profiling and SecurityContext integration. Only capabilities confirmed for a release become acceptance requirements for that version.
- Validate telemetry with an actual receiver and document the compatible scope.

Java follows a migration path that preserves the former repository while importing its complete history into the new repository. The migration must verify access permissions, former user entry points, and inherited workflows. See the [Java project entry](languages.md#java) for the target repository and development documentation.

## Near Term: Complete the Python Development and Release Cycle

- A complete-source OpenTelemetry Python Contrib downstream project has been established, preserving the former `gtrace` enhancement history and incorporating a pinned official baseline. See the [Python project entry](languages.md#python) for current development status.
- Validate the complete upstream test matrix, Beacon-specific enhancements, and the DataKit ingestion path, then define the actually supported Python environments and limitations.
- Finalize Beacon product packages, build and release processes, and upgrade and rollback procedures. Add version-specific user documentation after the initial official release.

## Later: Develop Go

- Inventory existing implementations and select the upstream project, source or dependency maintenance model, and enhancement scope.
- Establish build, test, upstream-tracking, and release processes.
- Add language onboarding documentation and actual support status under the shared maintenance principles.

The complete-source downstream approach used by Java has also been adopted for Python and PHP Contrib, but Go does not need to reuse the same branch layout, packaging, or feature list. Languages may progress independently according to available resources and maturity, and each completes its own validation and release.

## Later: Develop Node.js

- Base the project on the official [OpenTelemetry JavaScript Contrib](https://github.com/open-telemetry/opentelemetry-js-contrib) repository and merge the latest official upstream changes available when development begins.
- Validate the merged source, record the exact adopted commit or version, and identify its license, accompanying core dependencies, and any Beacon-specific differences to maintain.
- Decide the Beacon Node.js project location, integration model, and Beacon-specific enhancement scope.
- Establish build, test, upstream-tracking, and independent release processes. Validate target Node.js environments and an actual ingestion path before claiming support.

## Later: Complete PHP Validation and Release

- Complete-source downstream projects have been established separately for OpenTelemetry PHP Contrib and the native extension. Beacon PHP Instrumentation `0.1.0` is published, and component packages are tested against its fixed release commit. See the [PHP project entry](languages.md#php) for current development status.
- Validate the target PHP versions, extension versions, and initial component instrumentations, including an actual ingestion path.
- Finalize the Composer packages' official versioning, publishing permissions, and upgrade and rollback procedures. Add version-specific user documentation after the initial official release.

## As Real Needs Emerge

- Upstream update detection and synchronization assistance.
- Multi-language onboarding examples and a documentation site.
- Validated guidance for service identity, context, Profiling, and security-data correlation.

The roadmap does not assume a unified runtime, lockstep cross-language releases, a remote-control platform, or a new installation and injection system. New work must address a concrete user or maintenance need.
