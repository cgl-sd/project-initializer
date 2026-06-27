# Project Initializer

[中文](#中文) | [English](#english)

<details id="中文" open>
<summary>中文</summary>

## 简介

Project Initializer 是一个 Codex 技能，用来把项目文件夹整理成清晰、保守、可维护的结构。它适用于文献资料项目、研究笔记项目、代码/文档混合项目，以及需要同时保存参考资料、外部代码、讨论记录和工作区的项目。

这个技能的核心原则是：先检查，再整理；保留用户内容；只创建当前项目真正需要的目录。

## 仓库与 Skill 结构

```text
.
├── README.md
└── project-initializer/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

- `README.md`：GitHub 仓库说明，包含中文和英文两个可切换版本。
- `project-initializer/`：真正的 skill 文件夹，文件夹名与 skill 名称一致。
- `project-initializer/SKILL.md`：Project Initializer 技能定义和工作规则。
- `project-initializer/agents/openai.yaml`：技能在 OpenAI/Codex 环境中的展示与默认提示配置。

说明：按照 Codex skill 约束，skill 文件夹本体不放额外的 `README.md`、安装指南或变更日志等辅助文档。这个 README 只属于 GitHub 仓库根目录。

## 使用方式

将 `project-initializer/` 文件夹作为一个 Codex skill 安装或放入你的 Codex skills 目录后，可以在项目中请求：

```text
Use $project-initializer to initialize this project.
```

也可以直接用自然语言描述你的整理目标，例如：

```text
请用 project-initializer 整理这个项目，保留现有内容，并创建一个根 README。
```

## 技能会做什么

- 保留用户已有内容，除非用户明确要求删除。
- 默认只保留一个项目自有的根 `README.md`。
- 将顶层目录整理为两位数字前缀，例如 `00_reference/`、`01_external_code/`。
- 将参考资料、外部代码、讨论记录、项目工具和工作区放到合适的位置。
- 保留第三方代码、下载仓库或已创建技能内部自带的 README 文件。

## 默认目录模式

技能会根据项目实际内容选择需要的目录，而不是强行创建完整模板：

```text
00_reference/
01_external_code/
02_discussions/
03_project_tools/
04_workspace/
```

</details>

<details id="english">
<summary>English</summary>

## Overview

Project Initializer is a Codex skill for organizing project folders into a clear, conservative, and maintainable structure. It is useful for literature projects, research notes, code/documentation projects, and mixed projects that need to preserve references, external code, discussion records, and active work.

Its core principle is simple: inspect first, preserve user content, and create only the folders that the current project actually needs.

## Repository And Skill Structure

```text
.
├── README.md
└── project-initializer/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

- `README.md`: GitHub repository documentation with switchable Chinese and English versions.
- `project-initializer/`: The actual skill folder. Its folder name matches the skill name.
- `project-initializer/SKILL.md`: The Project Initializer skill definition and workflow rules.
- `project-initializer/agents/openai.yaml`: Display metadata and the default prompt for OpenAI/Codex environments.

Note: Codex skill constraints keep auxiliary documentation such as `README.md`, installation guides, and changelogs out of the skill folder itself. This README belongs only to the GitHub repository root.

## Usage

After installing the `project-initializer/` folder as a Codex skill, or placing it in your Codex skills directory, ask Codex to use it:

```text
Use $project-initializer to initialize this project.
```

You can also describe the desired organization in natural language, for example:

```text
Use project-initializer to organize this project, preserve existing content, and create one root README.
```

## What The Skill Does

- Preserves existing user content unless deletion is explicitly requested.
- Keeps one project-authored root `README.md` by default.
- Organizes top-level directories with two-digit prefixes, such as `00_reference/` and `01_external_code/`.
- Places reference materials, external code, discussion records, project tools, and workspace files in suitable locations.
- Preserves README files that belong to third-party code, downloaded repositories, or created skills.

## Default Directory Pattern

The skill creates only the directories that are useful for the current project instead of forcing a full template:

```text
00_reference/
01_external_code/
02_discussions/
03_project_tools/
04_workspace/
```

</details>
