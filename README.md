# Beacon

Beacon is a multi-language application instrumentation agent based on OpenTelemetry. Each language is developed and released independently; refer to the corresponding language documentation for its capabilities and support scope.

This repository is the product and documentation entry point. It does not contain agent implementations.

Each language evolves independently: .NET has an official release; Java, Node.js, Python, and PHP remain under development and validation; the Go project has not yet been established. Project entry points and current status are maintained in [Language Projects](docs/languages.md).

## Documentation

- [Language Projects](docs/languages.md): language repositories, development documentation, and release status.
- [Maintenance Principles](docs/maintenance.md): repository boundaries, upstream synchronization, and release requirements.
- [New Language Onboarding and Initial Release Guide](docs/language-onboarding.md): a reusable decision and validation guide for future languages.
- [Roadmap](docs/roadmap.md): future development directions, not commitments to supported capabilities or delivery dates.

## Using This Repository

- To use an agent: after an official release, find installation instructions, configuration, and support scope through its language entry.
- To develop an agent: modify code, synchronize upstream changes, run tests, and create releases in the corresponding language repository.
- To maintain product documentation: update language entry points, shared policies, and cross-language support information in this repository.

Language versions evolve independently. This repository does not define a unified Beacon product version.
