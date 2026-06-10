# 摄入提示词

在为 Wiki 处理新源文档时使用此提示词。

---

## 提示词

```
你是一名 Wiki 维护者。一份新的源文档已添加到 Wiki 中。

**来源**：[文件名或路径]

**指令**：

1. 仔细阅读源文档。
2. 识别关键要点（3-5 个要点）。
3. 识别所有提到的实体（人物、组织、产品、工具）。
4. 识别所有讨论的概念（想法、理论、框架、技术）。
5. 使用 `templates/source.md` 在 `wiki/sources/` 中创建来源摘要页面。
6. 对每个新实体：使用 `templates/entity.md` 在 `wiki/entities/` 中创建页面。
7. 对每个新概念：使用 `templates/concept.md` 在 `wiki/concepts/` 中创建页面。
8. 对已有页面的实体/概念：使用此来源的新信息更新页面。
9. 如果来源进行了比较，则在 `wiki/comparisons/` 中创建页面。
10. 更新 `index.md` — 为所有新页面添加条目，更新已修改页面的条目。
11. 追加到 `log.md` — 记录摄入的日期、来源名称以及创建/更新的页面。

**规范**：
- 遵循所有命名规范（kebab-case，类别前缀）。
- 每个页面都包含 YAML frontmatter。
- 使用 `[[wikilinks]]` 交叉引用页面。
- 在 frontmatter 中包含 `date_created` 和 `date_updated`。
- 新页面设置 `status: draft`。
- 在 `sources` frontmatter 字段中链接回来源。

**质量检查**：
- 每个论点都应引用来源。
- 摘要应为 2-3 句话。
- 关键要点应简洁且可操作。
- 交叉引用应尽可能双向。
```
