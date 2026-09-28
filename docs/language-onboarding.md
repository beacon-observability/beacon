# New Language Onboarding and Initial Release Guide

This guide captures a reusable decision sequence learned while preparing the Java, Python, and PHP projects. It is not a mandatory implementation template for every language, nor does it imply that any language under evaluation has an established project, supported capabilities, or a committed release plan. Language-specific baselines, commands, tests, and release procedures belong in the repositories linked from [Language Projects](languages.md).

## Define Boundaries Before Creating a Repository

1. Identify the requested language, upstream project, Beacon-specific capabilities to preserve, and all existing code sources. Inventory former packages and commands, licenses, compatibility, and migration impacts. Keep historical implementation status separate from new product capabilities.
2. Select a maintenance model appropriate to the language. Complete-source downstream maintenance, extending an upstream dependency, and other approaches all require an explicit rationale. Java, Python, and PHP Contrib use complete-source downstream maintenance, but other languages need not follow them. PHP also depends on a separately maintained native extension, demonstrating that one language may combine several maintenance models. Using a GitHub fork and preserving upstream history are separate decisions.
3. Define an independent repository and upstream provenance for the language project. Preserve traceable history and pin upstream versions, commits, and key dependencies. Keep synchronization, build, and test instructions in the language repository; this repository only provides entry points and shared principles.
4. Assign the language its own release scope, maintainers, and publishing permissions. Do not assume lockstep releases or a unified Beacon version.

## Establish a Reproducible Synchronization Process

- Record official upstream sources, historical Beacon-specific code, and the Beacon mainline separately. Verify the adopted release tag and complete commit, together with key dependencies. Do not write only "track the latest version" or infer an adopted baseline from the current upstream main branch.
- Preserve traceable upstream history and Beacon-specific differences during the initial import and every later update. Evaluate upstream changes and conflicts first, then synchronize, adapt, and run regression tests on an isolated branch. Never overwrite downstream enhancements with a fresh upstream directory. After adopting a baseline, update the language repository's provenance record and dependency pins.
- Reassess inherited build, CI, and publishing configuration during every synchronization to prevent upstream package names, release destinations, or credential flows from being used for Beacon. Keep synchronization steps, conflict handling, and validation commands in the language repository. Fetching or merging code alone does not mean validation has passed or a release is ready.

## Define Product Identity, Artifacts, and Versions

- Use Beacon plus the language name consistently in public material. Before choosing registered package, command, or module names, verify package-index ownership, ecosystem conventions, and migration cost. Historical brands are provenance information, not Beacon releases.
- List the actual artifacts in the initial release, their names, publication channels, and required or optional relationships. Check for conflicts with existing projects and define migration from former packages. Whether Profiling or another capability ships separately depends on that language's implementation and validation; Python's package structure does not automatically apply elsewhere.
- Distinguish the Beacon release version from upstream versions. The former identifies released Beacon artifacts; the latter records their baseline. They are related but not interchangeable. If a language produces several Beacon artifacts, state whether they share a version and how their consistency is verified.
- Release candidates, official releases, source tags, and package-index artifacts have separate states. Only an artifact that has actually been published and accepted can receive an official installation entry. Pushed code, a successful wheel or archive build, or a candidate version number does not constitute a release.

## Build from Pinned Source and Inspect Artifacts

- Define the build entry point and actual deliverable formats in the language repository, such as ecosystem packages, executable archives, or container images. Do not impose one package structure on every language. Build inputs must pin verified source commits, upstream baselines, and dependency sources, and must identify which files and Beacon-specific enhancements enter the artifact.
- Inspect artifact names, versions, dependency constraints, entry points, licenses, and required metadata. For multiple artifacts, also validate dependency and version relationships. Release the same artifacts that passed validation rather than rebuilding different artifacts afterward.
- Install and run candidate artifacts in clean environments, not only from the source tree. Record artifact digests. After publication, reinstall from the official channel and validate again. Detailed packaging tools and commands belong in the language repository.

## Advance the Initial Release Through Evidence

| Stage | Required evidence | Claims that the evidence does not support |
| --- | --- | --- |
| Provenance established | Upstream and Beacon-specific sources, pinned commits, and license review | Compatibility with all future upstream versions |
| Code synchronized | Adopted baseline, Beacon-specific differences, conflict handling, and affected tests | A completed merge means the project is release-ready |
| Packaging passed | Candidate artifacts built from pinned source, with names, versions, dependencies, and metadata | Artifacts have been published or are production-ready |
| Local validation | Beacon-specific regression tests plus clean installation and startup in target environments | The complete upstream matrix or ingestion path has been validated |
| Ingestion acceptance | Telemetry validation tied to the actual receiver, declared protocol, and version | Untested environments and capabilities are also supported |
| Official release | Pinned tag, immutable artifacts, release notes, known limitations, and rollback procedure | Other languages automatically provide the same capabilities |

Before publishing to a package index, verify that the public package name is available. Every release mechanism must have confirmed publishing permission and approval, upgrade, and rollback paths. After release, install again from the public index or download entry and add links to the pinned documentation and GitHub Release in [Language Projects](languages.md). If publication fails, do not overwrite an already published artifact with the same version; issue a new version according to the ecosystem's rules.

## Keep CI and Release Automation to the Minimum Needed

- Daily CI should focus on declared runtime support and Beacon-specific changes. Broader testing required for an upstream synchronization may run separately and must not automatically turn inherited upstream publishing workflows into Beacon release entry points. Before adding a workflow, identify its consumer, what it validates, its execution cost, and its permission boundaries.
- Separate queue time from execution time. If jobs remain `queued`, investigate runner availability, organization settings, concurrency, and quotas before reducing matrices or duplicate builds. Moving to a self-hosted server may remove queue delays, but one server may serialize previously parallel jobs, so faster completion cannot be promised without measurement.
- Pull requests in public repositories execute untrusted external code and must not run directly on long-lived self-hosted runners with access to internal resources. When self-hosting is necessary, design isolation, least privilege, and teardown after each job, then validate the design at actual capacity. Isolate release credentials from ordinary pull-request testing.
- Release workflows must validate pinned tags and artifacts and separate build-and-test permissions from upload permissions. Use identities and manual approvals appropriate to each publication channel. Before releasing multiple artifacts from one workflow, verify that the platform permits them to share a publishing identity. The PyPI Trusted Publisher and GitHub Environment setup currently used by Python is language-specific and must not be copied automatically.

## Document Only Actual Status

- A language repository README presents the product and development entry points. If confirmed Beacon contributors need to be shown, list only verified names and avatars; do not mix provenance, old commits, or automatic statistics into a contributor display. Git history and baseline records are the source of truth for code provenance.
- Development documentation may link to a branch, but it must state that the content can change. Official installation, support scope, and validation conclusions must link to a release tag or pinned commit. Before an official release, label the project "under development" and do not present development installation examples as official installation entry points.
- Update this product repository with language entry points and current status. Keep version details, complete test matrices, upstream synchronization commands, and release procedures in the language repository to prevent the two sources from drifting.

When onboarding another language, make these decisions and collect the required evidence before introducing new tools, manifests, or automation. Do not copy a process solely because an existing language has it. See [Maintenance Principles](maintenance.md) for shared constraints.
