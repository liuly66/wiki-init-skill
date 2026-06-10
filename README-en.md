<p align="center">
  <b>🇬🇧 English</b> | <a href="README.md">🇨🇳 中文</a>
</p>

<h1 align="center">wiki-init</h1>

<p align="center">
  🎯 One command to let AI build your entire knowledge base scaffold
</p>

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="license">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-blue" alt="platform">
</p>

---

## What is this?

Based on [Karpathy's LLM Wiki](https://github.com/karpathy/llm-wiki) three-layer architecture, **one instruction** lets AI automatically create a complete knowledge base scaffold with 18 files.

```
vault/
├── raw/          ← Layer 1: Raw documents (you put here)
├── wiki/         ← Layer 2: AI-generated wiki pages
├── templates/    ← Page templates
└── prompts/      ← Operation prompts
```

## Quick Start

### Install

Just place the `wiki-init/` directory into your Hermes skills folder. No extra dependencies needed.

### Usage

Simply tell your AI:

```
Initialize this directory using wiki-init: /path/to/your/vault
```

That's it. AI will automatically create the complete directory structure and all files.

## Prompt Tips

| Scenario | What to say |
|----------|-------------|
| 📁 Init project | `Use wiki-init to initialize D:\my-vault` |
| 📝 Import docs | `Use wiki-ingest to process all documents in raw/` |
| 🔍 Query knowledge | `What concepts about XX exist in this project?` |
| 🔄 Regenerate | `Rebuild the entities pages in wiki/` |

## Workflow

```
wiki-init creates scaffold → Drop docs into raw/ → wiki-ingest processes into wiki pages
```

## Who is this for?

- 📓 People using Obsidian / Markdown for notes
- 🤖 Anyone who wants AI to auto-organize and connect knowledge
- 🧠 Knowledge management and second-brain enthusiasts

## Related Projects

- [wiki-ingest](https://github.com/liuly66) — Batch import content into the scaffold
- [llm-wiki](https://github.com/karpathy/llm-wiki) — Karpathy's original project

## License

MIT
