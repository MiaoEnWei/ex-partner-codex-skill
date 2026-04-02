# 前任 Skill for Codex / 前任 Codex Skill

[![GitHub release](https://img.shields.io/github/v/release/Cz1ang/ex-partner-codex-skill)](https://github.com/Cz1ang/ex-partner-codex-skill/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Codex Skills](https://img.shields.io/badge/Codex-Skills-blue)](./skills)

这是一个面向 **Codex** 的 **前任 skill** 项目，用来把“前任 / 前对象 / 旧关系对象”整理成可持续更新的 persona skill。

本项目基于上游项目进行 Codex 定向二次开发：

- https://github.com/therealXiaomanChu/ex-skill

它不是上游仓库的原样镜像，而是在上游 `ex-skill` 的产品思路、交互流程、模板和脚本基础上，针对 **Codex** 做的适配开发与重新封装。

---

## 功能特性

### 数据源

| 来源 | 格式 | 备注 |
|---|---|---|
| 微信聊天记录 | WeChatMsg / 留痕 / PyWxDump 导出 | 推荐，信息最丰富 |
| QQ 聊天记录 | txt / mht 导出 | 适合学生时代的恋情 |
| 朋友圈 / 微博 | 截图 | 提取公开人设 |
| 照片 | JPEG / PNG（含 EXIF） | 提取时间线和地点 |
| 口述 / 粘贴 | 纯文本 | 你的主观记忆 |

### 生成的 Skill 结构

每个前任 Skill 由两部分组成，共同驱动输出：

| 部分 | 内容 |
|---|---|
| Part A — Relationship Memory | 共同经历、约会地点、inside jokes、争吵模式、甜蜜瞬间、关系时间线 |
| Part B — Persona | 5 层性格结构：硬规则 → 身份 → 说话风格 → 情感模式 → 关系行为 |

### 运行逻辑

收到消息后：

1. **Persona** 先判断 ta 会怎么回  
2. **Memory** 再补充你们之间的共同记忆  
3. 最终**用 ta 的方式输出**

### 支持的标签

- **依恋类型**：安全型、焦虑型、回避型、混乱型
- **爱的语言**：肯定的言辞、精心的时刻、接受礼物、服务的行动、身体的接触
- **性格标签**：话痨、闷骚、嘴硬心软、冷暴力、粘人、独立、浪漫主义、实用主义、完美主义、工作狂、控制欲、没有安全感、报复性熬夜、已读不回、秒回选手、朋友圈三天可见、半夜发语音等
- **星座**：十二星座全支持
- **MBTI**：16 型全支持

### 进化机制

1. **追加记忆**  
   找到更多聊天记录 / 照片 → 自动分析增量 → merge 进对应部分

2. **对话纠正**  
   说 `ta不会这样说` → 写入 Correction 层 → 立即生效

3. **版本管理**  
   每次更新自动存档，支持回滚

---

## 安装

### 项目安装（推荐）

Codex 优先从 git 仓库根目录的 `.codex/skills/` 查找项目级 skill。

在 git 仓库根目录执行：

```bash
bash ./install-to-project.sh
```

安装后结构类似：

```text
<repo>/.codex/skills/
  create-ex/
  list-exes/
  delete-ex/
  let-go/
  ex-rollback/
```

### 全局安装

```bash
bash ./install-global.sh
```

默认安装位置：

```bash
${CODEX_HOME:-$HOME/.codex}/skills
```

### 可选依赖

```bash
pip3 install -r requirements.txt
```

目前唯一的可选依赖是 `Pillow`，主要用于照片 EXIF 分析。

---

## 使用

在 Codex 中输入：

```text
create-ex
```

按提示输入前任的：

- 代号
- 基本信息
- 性格画像
- 数据来源

即使只有文字描述，也可以先生成第一版。

完成后使用生成的 runtime skills：

```text
ex-<slug>
ex-<slug>-memory
ex-<slug>-persona
```

后续管理可使用：

- `list-exes`
- `ex-rollback <slug> <version>`
- `delete-ex <slug>`
- `let-go <slug>`

---

## 包含内容

- `skills/create-ex` — 主技能
- `skills/list-exes` — 列出已生成角色
- `skills/delete-ex` — 删除角色
- `skills/let-go` — 温柔删除别名
- `skills/ex-rollback` — 版本回滚
- `install-to-project.sh` — 项目安装脚本
- `install-global.sh` — 全局安装脚本
- `requirements.txt` — 可选依赖声明

---

## 分语言文档

- 中文详细版：[README_CN.md](./README_CN.md)
- English version: [README_EN.md](./README_EN.md)

---

## 仓库结构

```text
.
├── README.md
├── README_CN.md
├── README_EN.md
├── LICENSE
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
