---
name: project-initializer
description: Initialize or reorganize text/script and software projects while preserving user content. Use for project initialization, standardization, or cleanup. Establish README, AGENTS, CHANGELOG, .gitignore and tmp, docs, src; apply software-specific guidance naming, Git commits, ongoing records, and post-change compilation for Android Studio/Xcode apps.
---

# Project Initializer

Apply these rules to the target project, not to this skill package merely because it is being edited. Explicit user instructions override defaults, including instructions to defer commits. Preserve existing content and unrelated user work; archive extraction/deletion and a particular IDE are task-specific requirements, not automatic initialization steps.

## Project Category

Classify by the main deliverable and the user's goal:

- **Text/script:** reference collections, notes, reports, standalone or research scripts, and notebook experiments.
- **Software:** apps, websites, games, and other software products, including products implemented in scripting languages.

The presence of executable code alone does not imply software development. For mixed projects, ask only if the category remains unclear and changes the required behavior.

## Shared Requirements

### Root Files

Establish or update these four root files without discarding existing content:

- `README.md`: project purpose, actual structure, configuration, and usage.
- `AGENTS.md`: category and applicable persistent requirements, so later conversations can follow them.
- `CHANGELOG.md`: change-record entrypoint.
- `.gitignore`: required for both categories even before Git is used. Preserve existing rules and, by default, ignore large files, all root `docs/` contents, and all root `tmp/` contents including test files, plus secrets, machine-specific configuration, caches, and build outputs. Keep ordinary source files and the required root documents eligible for version control. Apply explicit user exceptions when requested. Identify large files from actual project contents and use concrete paths or suitable artifact patterns; do not invent a fixed size threshold or exclude all binary resources blindly. Git ignore rules do not implement size-based filtering.

Do not casually add more project-authored documentation. Create new documents only at root; subdirectory documents, including README files, require an explicit user request. Preserve existing guidance and upstream documents inside repositories, packages, and skills. Relocating existing guidance to `docs/` is organization, not permission to generate more documents there.

### Required and Optional Directories

Establish all three directories at root, even when initially empty:

```text
tmp/    # All test files
docs/   # Existing text guidance; new guidance only on explicit request
src/    # Source files and scripts
```

Use descriptive names without numeric prefixes for any additional directories. Optional examples are `reference/` for separate reference materials and `external_code/` for independent third-party reference repositories. Create them only when needed; check both names and purposes against existing directories and reuse suitable locations instead of duplicating them. Optional directories must not replace the required three.

Place existing tests, text guidance, and source files in their respective locations, preserving content and updating links and build/test discovery paths. Do not invent guidance or placeholder tests to fill empty directories. Keep test files available locally even though `tmp/` is ignored by default; ignoring a file does not authorize deleting it.

Retain framework module names and necessary build files. Integrate source/test placement through supported configuration. If root `src/` placement conflicts with Android/Xcode or other framework paths and cannot be reconciled without a consequential structural change, explain the specific conflict and obtain the user's choice before moving those files. Do not silently waive the directory rule or break the build.

### Git Conventions When Git Is Used

Reuse an existing repository, branches, history, and identity settings. Check the default exclusions above and the staged diff. Use root-anchored `/docs/` and `/tmp/` patterns for these project directories. Ignore rules do not untrack existing files: if an excluded file is already tracked, report that fact and obtain authorization before changing its tracking state; preserve the local file and do not rewrite history. Commit relevant eligible task changes without including unrelated user changes. Do not force-add default-ignored local files merely to satisfy the commit requirement. When only ignored local files changed and no applicable record update is needed, report that no committable changes remain rather than creating an empty commit. Use Chinese commit messages for both project categories and follow additional user Git requirements. Do not create empty commits. Committing does not authorize pushing or creating a remote repository.

## Software-Specific Requirements

- **Guidance naming:** give existing development-guidance files clear, descriptive names. Text/script projects use the same `docs/` location but do not require renaming.
- **Initial commit:** after establishing the initial root files (including `.gitignore`) and required directories, make the initial project-setup commit immediately; do not wait for acceptance or environment verification. Prepare necessary ignore rules first. Existing repositories receive a setup-change commit when appropriate, not a new repository or rewritten history. Repeated initialization with no new changes needs no commit.
- **Later commits:** at the end of every conversation that produces project changes, commit the remaining changes before the final response. Text/script projects use Git situationally and require neither an initial nor a per-conversation commit. Explicit user instructions to prohibit or defer commits take precedence.
- **Ongoing records:** update `AGENTS.md` for major constraints, `CHANGELOG.md` for significant changes and verification results, and `README.md` when structure, setup, or usage changes. Update the affected documents before the corresponding commit; do not repeat the same account in all three. Text/script projects require the initial root files but ongoing updates are optional unless requested.
- **Native application verification:** apply the Android Studio/SwiftUI/Xcode requirements below before the end-of-conversation change commit and final response. The initial setup commit still precedes acceptance; explicit user overrides apply.

In software `AGENTS.md`, persist the shared structure, test-location, root-document and default-ignore rules, plus Chinese commit messages, per-conversation commits, ongoing records, and applicable build/install/relaunch requirements. Do not impose these software-only obligations on text/script projects.

## Android Studio and SwiftUI/Xcode Applications

Apply these requirements when initializing or changing native applications. Adapt to the existing project; do not impose another application's product rules, exact layer names, tool versions, or device model.

- **Local environment first:** inspect installed IDE/toolchain versions, SDKs, runtimes, devices, and dependency caches against the project's declared requirements. Reuse compatible local installations; obtain only missing required components after establishing what is missing or incompatible. Avoid optional source/documentation downloads or unrelated SDK installations. Respect the user's chosen IDE/window and integrated device workflow.
- **Engineering configuration:** for Android, preserve the Gradle Wrapper, module configuration, Manifest, resources, and variant settings; update `sourceSets` when source/test paths change. For Xcode, identify the project/workspace, target, scheme, configuration, source/resource membership, and dependencies. If an existing generator such as XcodeGen owns the project, modify its authoritative specification and regenerate through the established workflow rather than editing only generated files.
- **Compatibility and identity:** retain the minimum supported OS, declared tool/dependency versions, application identifier, signing, entitlements, and permission configuration unless the task requires a change. Check new APIs against the existing minimum OS; do not silently raise it to resolve a build error. Request a user decision for changes that alter supported platforms or application identity beyond the authorized task.
- **Code and data boundaries:** follow the existing separation of UI, business rules, and data access. Keep complex persistence/business logic out of Compose or SwiftUI view code. Preserve user data during verification; keep demo/test data out of production initialization. Do not reset app storage or uninstall as a routine verification step. Where builds depend on generated resources or a local service, verify the existing generation/service workflow when affected.
- **Build and run the new artifact:** after changes, compile the affected application, install that build on the chosen available simulator/emulator/device, terminate the old app process, and launch the new build. For desktop SwiftUI applications, launch the newly built executable instead of installing to a mobile simulator. Reuse the user's running device when suitable. For UI changes, inspect the changed screens and interactions; previews, IDE sync, compilation, or merely opening a simulator are not substitutes for running the new artifact.
- **Evidence and failures:** keep validation logs/screenshots and other disposable verification outputs under `tmp/`, apart from maintained tests. Fix change-induced build/run errors and repeat the affected verification. Report build, installation, launch, and UI/behavior checks separately. If environment, dependency, signing, or device availability blocks a step, state the exact limitation and unfinished checks; never claim runtime acceptance from a successful build alone.

## Execution Order and Final Checks

1. Inspect the target tree, instructions, framework configuration, and Git status. Classify the project and identify protected or unrelated content.
2. Establish the four root files and required directories. For software projects, make the initial setup commit at this point, subject to explicit user overrides.
3. Organize remaining existing content and configure affected paths. Verify preservation, distinct directory purposes, documentation scope, and build/test discovery. Build, install, relaunch, and inspect native applications after changes as required above.
4. Complete the applicable records and remaining commits. Report what changed, verification results and limitations, and Git status. Do not claim a push occurred unless authorized and completed.

Git does not track empty directories: distinguish directories established locally from contents actually recorded in a commit, and do not add filler documents to bypass the documentation rule. On case-insensitive filesystems, use an intermediate filename for case-only renames.
