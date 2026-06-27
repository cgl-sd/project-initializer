---
name: project-initializer
description: Initialize or reorganize a project folder into a flexible numbered structure while preserving user content. Use when the user asks to create, initialize, standardize, or clean up a project for either (1) text/reference-document projects or (2) code/documentation projects. Enforce one project-authored root README by default while allowing upstream README files inside downloaded external code or installed/created skills, numbered top-level directories, optional reference and external-code organization when those contents exist, discussion/project-tool placement, and a final workspace when active work areas are needed.
---

# Project Initializer

Initialize projects without forcing every project into the same rigid template. This skill applies a few hard rules, then adapts the structure to the project’s actual contents.

## Suitable Project Types

Use this skill for two broad project forms:

1. Text/reference-document projects
   - Literature collections.
   - Research notes.
   - Reports, drafts, outlines, and reading records.
   - Reference PDFs, Word files, bibliographies, or archived documents.

2. Code/documentation projects
   - Python or notebook experiments.
   - External repositories used as references.
   - Project documentation plus implementation work.
   - Mixed research projects with papers, code, notes, and experiments.

## Hard Rules

Always preserve user content. Do not delete files unless the user explicitly asks.

1. Keep one project-authored root `README.md` by default.
2. Number every top-level directory with a two-digit prefix, such as `00_`, `01_`, `02_`.
3. If reference materials exist, organize them into a numbered reference directory.
4. If external or third-party code exists, organize it into a numbered external-code directory.
5. Give discussion records and project-maintenance scripts suitable numbered locations.
6. If a workspace is needed, place it last among numbered top-level directories.

Do not require a personal/user-content folder. Create it only if the user asks or the project clearly needs one.

Exception to the README rule: preserve README files that belong to downloaded external code, GitHub repositories, created/downloaded skills, or other third-party packages. Do not rename or delete upstream README files merely to satisfy the project-authored README convention.

## Flexible Directory Pattern

Use this pattern as a default, not as a mandatory template:

```text
00_reference/
01_external_code/
02_discussions/
03_project_tools/
04_workspace/
```

Create only directories that are useful for the current project.

- `00_reference/`: papers, reports, books, bibliographies, reference datasets, original archives, and other reference materials.
- `01_external_code/`: cloned repositories and third-party code that should remain distinct from user-authored code.
- `02_discussions/`: reading notes, research ideas, meeting notes, discussion records, planning notes, and conversation-derived Markdown.
- `03_project_tools/`: helper scripts for organizing, checking, renaming, inventorying, or maintaining the project. These are not the user’s research/source code.
- `04_workspace/`: active work such as code, project documents, experiments, derivations, drafts, or implementation tasks.

Do not create a default `shared/` folder. Common material should go where it naturally belongs: reference, external code, discussions, project tools, or a concrete workspace task.

## README Guidance

The root `README.md` should be concise and should explain:

- What the project is for.
- Which of the two broad forms it mainly follows:
  1. text/reference-document project;
  2. code/documentation project.
- The current numbered directory structure.
- What each directory is used for.
- Any important constraints, such as archives not being extracted or third-party code not being modified.

Do not create additional project-authored README files in subdirectories by default. However, if third-party code, downloaded repositories, or created/downloaded skills already contain README files, keep them as-is.

If a user explicitly asks to avoid README filenames even in bundled/generated content, preserve the content by renaming it, for example:

```text
UPSTREAM_OVERVIEW.md
USER_EXAMPLE_OVERVIEW.md
PROJECT_ALPHA_OVERVIEW.md
```

For bilingual Markdown, prefer one of these approaches:

1. Single-file bilingual README, compatible with the default project-authored README rule:

   ```text
   README.md
   ```

   Use paired sections that can be swapped or edited independently:

   ```markdown
   # Project Title

   中文说明：……

   English summary: ...

   ## 目录结构 / Directory Structure

   中文说明：……

   English summary: ...
   ```

2. Two-file bilingual project documentation only when the user explicitly relaxes the default project-authored README rule:

   ```text
   README.md
   README.zh-CN.md
   README.en.md
   ```

   In the default rule set, avoid this for project-authored documentation because it creates multiple README files. This does not apply to upstream README files inside external code or skills.

## Workflow

1. Inspect before changing.
   - List top-level files and directories.
   - Identify README-like files, PDFs, documents, archives, external source-code folders, notebooks, scripts, notes, and existing project metadata.
   - Respect user constraints such as “do not open ZIP files,” “do not touch this folder,” or “keep this area empty.”

2. Decide what exists.
   - If reference materials exist, create/use a numbered reference directory.
   - If external code exists, create/use a numbered external-code directory.
   - If discussion or research notes exist, create/use a numbered discussions directory.
   - If project-maintenance scripts are needed, create/use a numbered project-tools directory.
   - If active user work needs a home, create/use a final numbered workspace directory.

3. Move conservatively.
   - Preserve archives unless the user asks to extract them.
   - Keep external code separate from user-authored code.
   - Do not place agent/project-maintenance helper scripts inside workspace.
   - Do not move user work into a new personal folder unless requested.

4. Update root metadata.
   - `README.md`: project purpose, project form, structure, and usage rules.
   - `AGENTS.md`: agent/Codex boundaries and project-specific constraints.
   - `CHANGELOG.md`: structural changes, downloads, environment setup, and other maintenance actions.

5. Validate.
   - Confirm only one project-authored root README exists by default.
   - Confirm upstream README files inside external code or skills were preserved unless the user explicitly requested otherwise.
   - Confirm every top-level directory is numbered.
   - Confirm protected files/folders were not changed.
   - Confirm workspace is last if it exists.

## Safety Rules

- Ask before deleting, overwriting, extracting archives, or modifying third-party source code.
- Prefer rename-and-preserve over delete.
- Do not run project code, notebooks, training, or examples unless the user explicitly asks.
- Lightweight import/version checks are acceptable only when they are part of environment setup and do not execute project logic.
- If the filesystem is case-insensitive, use a temporary name when changing only filename casing, such as `changelog.md` to `CHANGELOG.md`.
