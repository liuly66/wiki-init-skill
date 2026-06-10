<p align="center">
  <a href="README-en.md">🇬🇧 English</a> | <b>🇨🇳 中文</b>
</p>

<h1 align="center">wiki-init</h1>

<p align="center">
  🎯 一行命令，让 AI 帮你搭好整个知识库骨架
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="license">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-blue" alt="platform">
</p>

---

## 这是什么？

基于 [Karpathy LLM Wiki](https://github.com/karpathy/llm-wiki) 三层架构，**一条指令**让 AI 自动创建 18 个文件的完整知识库骨架。

```
vault/
├── raw/          ← 第一层：原始文档（你放）
├── wiki/         ← 第二层：AI 生成的知识页面
├── templates/    ← 页面模板
└── prompts/      ← 操作提示词
```

## 快速开始

### 安装

把 `wiki-init/` 目录放到你的 Hermes skills 目录下即可，无需额外依赖。

### 使用

直接对 AI 说：

```
帮我用 wiki-init 初始化这个目录：/path/to/your/vault
```

就这样，AI 会自动创建完整的目录结构和所有文件。

## 提问技巧

| 场景 | 怎么说 |
|------|--------|
| 📁 初始化项目 | `帮我用 wiki-init 初始化 D:\my-vault` |
| 📝 导入文档 | `用 wiki-ingest 处理 raw/ 下的所有文档` |
| 🔍 查询知识 | `这个项目里关于 XX 的概念有哪些？` |
| 🔄 重新生成 | `重新整理 wiki/ 下的 entities 页面` |

## 工作流程

```
wiki-init 搭建骨架 → 往 raw/ 放文档 → wiki-ingest 处理成 wiki 页面
```

## 适合谁？

- 📓 用 Obsidian / Markdown 做笔记的人
- 🤖 想让 AI 帮你自动整理和关联知识的人
- 🧠 对知识管理和第二大脑感兴趣的人

## 相关项目

- [wiki-ingest](https://github.com/liuly66) — 往骨架中批量导入内容
- [llm-wiki](https://github.com/karpathy/llm-wiki) — Karpathy 原始项目

## License

MIT
