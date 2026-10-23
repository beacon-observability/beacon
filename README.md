# Beacon

Beacon combines OpenTelemetry-based server instrumentation, the fastrace Rust tracing library, and browser real user monitoring through Rumable. Each component is developed and released independently; refer to its versioned documentation for capabilities and support scope.

This repository is the product and documentation entry point. It does not contain component implementations.

Each language evolves independently: Java, Node.js, Python, and .NET have official releases; the
PHP native instrumentation has a component release; the complete PHP distribution remains under
development and validation; and the Go project has not yet been established. Beacon Security is
released as an opt-in capability in the existing Java, Python, and Node.js product packages.
Fastrace has its first official Beacon source release, `v0.1.0`, with fixed-tag SDK installation and local DataKit OTLP/gRPC acceptance.
Rumable has released browser RUM integration for Linux/Nginx and Windows/IIS as `v0.1.9`.
Project entry points and current status are maintained in
[Language and Browser Projects](docs/languages.md).

## Documentation

- [Language and Browser Projects](docs/languages.md): component repositories, development documentation, and release status.
- [Rumable browser RUM](docs/languages.md#rumable-browser-rum): browser monitoring, GitHub downloads, and the English configuration page.
- [Beacon Security Specification](https://github.com/beacon-observability/beacon-security-spec): the shared, language-neutral development contract for Security events, identity, configuration, fingerprints, and runtime SBOM data. It is not an implementation or release commitment.
- [Maintenance Principles](docs/maintenance.md): repository boundaries, upstream synchronization, and release requirements.
- [New Language Onboarding and Initial Release Guide](docs/language-onboarding.md): a reusable decision and validation guide for future languages.
- [Roadmap](docs/roadmap.md): future development directions, not commitments to supported capabilities or delivery dates.

## Using This Repository

- To use server instrumentation or browser RUM: after an official release, find installation instructions, configuration, and support scope through its project entry.
- To develop an agent: modify code, synchronize upstream changes, run tests, and create releases in the corresponding language repository.
- To maintain product documentation: update language entry points, shared policies, and cross-language support information in this repository.

Language agents and Rumable evolve independently. This repository does not define a unified Beacon product version.
