# Ex-Partner Codex Skill

[![GitHub release](https://img.shields.io/github/v/release/MiaoEnWei/ex-partner-codex-skill)](https://github.com/MiaoEnWei/ex-partner-codex-skill/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Codex Skills](https://img.shields.io/badge/Codex-Skills-blue)](./skills)

Codex-oriented adaptation and secondary development based on the upstream project:

- https://github.com/therealXiaomanChu/ex-skill

This repository packages a reusable Codex workflow for turning an ex-partner or past relationship into an editable persona skill using local memories, exports, and photos.

## Highlights

- Build a new ex-partner persona skill from text-only input or richer local artifacts
- Ingest WeChat, QQ, screenshots, photos, and pasted memories
- Generate 3 runtime skills:
  - `ex-<slug>`
  - `ex-<slug>-memory`
  - `ex-<slug>-persona`
- Support iterative correction, memory append, rollback, and deletion
- Prefer project-scoped `.codex/` installation inside a git repository

## Quick install

### Install into the current project

Run from your git repository root:

```bash
bash ./install-to-project.sh
```

This installs the bundled skills into:

```text
<repo>/.codex/skills/
```

### Or install globally

```bash
bash ./install-global.sh
```

Default global target:

```bash
${CODEX_HOME:-$HOME/.codex}/skills
```

### Optional dependency

```bash
pip3 install -r requirements.txt
```

## What’s included

- `skills/create-ex` — main builder workflow
- `skills/list-exes` — list generated personas
- `skills/delete-ex` — delete a generated persona
- `skills/let-go` — softer delete alias
- `skills/ex-rollback` — rollback to a previous version

## Documentation

- English: [README_EN.md](./README_EN.md)
- 中文: [README_CN.md](./README_CN.md)

## Upstream attribution

This project is a Codex-focused adaptation and packaging effort built on top of the ideas and workflow shape from the upstream `ex-skill` project. It is not a verbatim mirror of the upstream repository.

## Repository structure

```text
.
├── README.md
├── README_EN.md
├── README_CN.md
├── install-to-project.sh
├── install-global.sh
├── requirements.txt
└── skills/
    ├── create-ex/
    ├── list-exes/
    ├── delete-ex/
    ├── let-go/
    └── ex-rollback/
```
