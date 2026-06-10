---
name: wiki-init
description: "初始化 Karpathy LLM Wiki 三层架构项目（目录结构 + AGENTS.md + 模板 + 提示词 + README）。一次性操作，建好骨架后配合 wiki-ingest 使用。"
platforms: [linux, macos, windows]
tags: [obsidian, wiki, knowledge-management, llm-wiki, karpathy]
---

# Wiki 项目初始化

从零搭建符合 Karpathy LLM Wiki 模式的知识库项目骨架。

## 触发条件

- 用户说"初始化 wiki"、"新建 wiki 项目"、"搭建 wiki 骨架"
- 用户指定一个新的空目录要变成 wiki 项目
- 用户提供了 Obsidian vault 路径要求初始化

## 前置条件

- 目标目录已存在（可以是空目录，也可以只有 `.obsidian/`）
- 目标目录不在已初始化的 wiki 项目内

## 三层架构概览

```
vault/
├── AGENTS.md              # 架构文档（核心规范）
├── index.md               # 内容目录（空，待填充）
├── log.md                 # 活动日志（记录初始化）
├── raw/                   # 第一层：原始来源（不可变）
│   ├── README.md
│   └── assets/
├── wiki/                  # 第二层：LLM 生成的 Wiki 页面
│   ├── entities/          # 人物、组织、产品、工具
│   ├── concepts/          # 想法、理论、框架、技术
│   ├── sources/           # 源文档摘要
│   ├── comparisons/       # 比较分析
│   └── synthesis/         # 跨领域综合
├── templates/             # 页面模板
│   ├── entity.md
│   ├── concept.md
│   ├── source.md
│   └── comparison.md
└── prompts/               # 操作提示词
    ├── ingest.md
    ├── query.md
    └── lint.md
```

## 执行步骤

### 1. 确认目标路径

```python
# 验证目标目录存在
terminal(f"test -d '{target_path}' && echo OK || echo MISSING")
```

如果目录不存在，询问用户是否要创建。

### 2. 检查是否已初始化

检查目标路径下是否已有 `AGENTS.md`。如果有，询问用户是要**重新初始化**（覆盖）还是**取消**。

### 3. 创建目录结构

```bash
mkdir -p "{target}/raw/assets"
mkdir -p "{target}/wiki/entities"
mkdir -p "{target}/wiki/concepts"
mkdir -p "{target}/wiki/sources"
mkdir -p "{target}/wiki/comparisons"
mkdir -p "{target}/wiki/synthesis"
mkdir -p "{target}/templates"
mkdir -p "{target}/prompts"
```

### 4. 生成所有文件

按以下列表创建文件，内容见下方模板节：

**根目录文件：**
- `AGENTS.md` — 架构文档
- `index.md` — 空白内容目录
- `log.md` — 日志（记录初始化事件）

**raw/ 文件：**
- `raw/README.md`
- `raw/assets/.gitkeep`

**wiki/ 文件：**
- `wiki/README.md`
- `wiki/entities/README.md`
- `wiki/concepts/README.md`
- `wiki/sources/README.md`
- `wiki/comparisons/README.md`
- `wiki/synthesis/README.md`

**模板文件：**
- `templates/entity.md`
- `templates/concept.md`
- `templates/source.md`
- `templates/comparison.md`

**提示词文件：**
- `prompts/ingest.md`
- `prompts/query.md`
- `prompts/lint.md`

使用 `write_file` 批量创建，每个文件内容见下方模板。

### 5. 验证

```python
# 列出所有创建的文件（排除 .obsidian）
terminal(f"find '{target}' -type f -not -path '*/.obsidian/*' | sort | wc -l")
# 应该返回 18
```

### 6. 报告结果

向用户展示创建的目录树和后续使用说明。

## 模板内容

所有模板内容完整收录在 `references/templates/` 目录中。初始化时从 references 读取并写入目标路径。

## 与 wiki-ingest 的关系

| | wiki-init | wiki-ingest |
|---|---|---|
| 用途 | 从零搭建项目骨架 | 往骨架中填入内容 |
| 频率 | 一次性 | 反复使用 |
| 输入 | 空目录 | raw/ 中的文档 |
| 产出 | 18 个结构文件 | wiki 页面 |

**使用流程**：`wiki-init` 搭建骨架 → 往 `raw/` 放文档 → `wiki-ingest` 处理成 wiki 页面

## pitfalls

- 如果目标路径下已有 `.obsidian/`，不要删除它（用户可能已配置 Obsidian 设置）
- AGENTS.md 是核心文件，LLM 在执行任何 wiki 操作前都会读取它，所以必须完整且准确
- 初始化后 `index.md` 是空的，需要配合 `wiki-ingest` 填充
- 所有文件使用中文（与 llywork 项目保持一致），可根据用户需求调整语言
