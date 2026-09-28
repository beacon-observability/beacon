# Maintenance Principles

## Repository Responsibilities

| Content | Maintained in |
| --- | --- |
| Product overview, language entry points, cross-language support status, and shared principles | `beacon` |
| Language source, enhancements, configuration, tests, upstream baseline, builds, and releases | The corresponding language repository |
| Implementations and protocols for independent components such as SecurityContext | The component's own repository |
| Ingestion, processing, and platform presentation | DataKit and the corresponding platform projects |

Each fact has one authoritative source. The product repository links to language documentation and release records; it does not manually duplicate source commits, dependency versions, or checksums. Changes to cross-component interfaces are reviewed by the affected repositories. This repository only summarizes compatibility impacts relevant to users.

## Upstream Maintenance

- Select a maintenance model that fits each language. Languages are not required to copy the Java project structure.
- Java uses a complete-source downstream model, preserving the upstream layout and history while allowing native instrumentation enhancements. See the [Java project entry](languages.md#java) for synchronization, baseline, and release documentation.
- Node.js uses a standalone downstream copy of the complete OpenTelemetry JavaScript Contrib source and history, with Beacon-specific additions kept isolated. See the [Node.js project entry](languages.md#nodejs) for its baseline, synchronization, and release-preparation documentation.
- Python uses a standalone downstream copy of the complete OpenTelemetry Python Contrib source, preserving existing Beacon-specific commits and upstream history. See the [Python project entry](languages.md#python) for synchronization, baseline, and release-preparation documentation.
- Pin upstream versions and commits, keep Beacon-specific differences controlled, and maintain corresponding regression tests.
- Track official upstream updates. Evaluate changes, resolve conflicts, and validate before adoption; "always current" never means releasing an untested upstream update directly.
- Contribute generally useful fixes upstream whenever practical. Remove duplicate downstream implementations after an equivalent upstream solution has been validated.

Synchronization frequency and response targets depend on actual maintenance capacity. Complete and validate one synchronization cycle before automating it. No dedicated bot or fixed number of workflows is assumed.

## Independent Releases

Each language defines its own versions and release cadence. Java, Go, Node.js, Python, PHP, and .NET are not required to release together, and a language release does not require a new unified Beacon version.

Each language repository is responsible for:

1. Pinning release source and dependency provenance while retaining licenses and required third-party notices.
2. Validating the capabilities, runtime environments, and ingestion compatibility claimed for the release, including regression tests for Beacon-specific enhancements.
3. Publishing release notes, artifact verification data, known limitations, and rollback instructions.
4. Keeping published tags and artifacts immutable and issuing a new version for fixes.

At the initial official release, add the actual installation and release entry points to [Language Projects](languages.md). Later updates are required when an entry point or public support status changes; every patch release does not need to be recorded across repositories. The language repository's release records are authoritative for exact versions. If this repository refers to a specific version, it must retain that version identifier and must not imply that the statement applies to every subsequent release.

## Documentation Links

- Within this repository: use links relative to the current Markdown file. The target must be committed to this repository. Use [README](../README.md) to return to the project home page.
- Across repositories: use a complete HTTPS URL containing the organization and repository. File links must specify a branch, tag, or commit and must not depend on the local workspace layout.
- Development documentation: a development branch may be linked when the content is explicitly described as mutable. Official installation, compatibility, and validation documentation must link to the corresponding release tag or pinned commit.
- Before release: collect confirmed target locations on the language projects page and mark them as pending. Do not invent unknown URLs or provide placeholder download links.
- Before publishing: confirm that each target file has been committed and that the cross-repository URL is accessible to its intended readers. A valid URL shape, a same-named local file, or administrator access does not replace this check.
- When files or branches move, update their entry points and references together. Documentation must not depend on maintainers' absolute paths, sibling clones, or operating systems.

## Documentation and Support Commitments

- Describe supported, experimental, and planned capabilities separately.
- Use consistent, user-facing concepts across languages without forcing different runtimes to share implementation or configuration details.
- Publish performance overhead, synchronization targets, and support periods only after testing or maintainer confirmation; estimates are not guarantees.
- Add CI only for concrete synchronization, validation, and release needs. Workflow structure depends on execution cost and permission boundaries.
- Consider a combined version, unified installer, or generated product manifest only if a real unified-suite delivery need emerges.
