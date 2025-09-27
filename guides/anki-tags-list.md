命名建议：全部小写、短横，避免空格与中文 tag（便于命令/脚本一致操作）。
`chunk`
- 用途：短语 / collocation（例：roll clothes to save space）。
- 何时打：当你决定某个短语值得保留作 recall 时。一般优先低于 `upgrade`。

`function`
- 用途：功能性语言骨架（principle / reason / contrast 等）。
- 何时打：把骨架做成模板类提示卡（Prompt/Back 包含多个实例）时使用。

`upgrade`
- 用途：当天做出的“旧→新”升级句（优先级最高）。
- 何时打：把升级句做成 Cloze/Transformation 就标 `upgrade`，便于周内复盘与优先复习。

`transfer`
- 用途：迁移句 / 可迁移原则（principle → 另一个领域的句子）。
- 何时打：迁移句做成 Speaking Prompt 或 Cloze 时标记，用于检查迁移能否泛化。

`skeleton`
- 用途：P‑R‑E 等骨架提示（少量）。
- 何时打：仅当你把骨架做成卡（通常不建议大量做）时使用。

`ladder`
- 用途：表达升级阶梯相关卡（可选）。
- 何时打：做 transformation 练习卡时使用。

`temp`
- 用途：候选卡，试用期（例如 7 天）。
- 何时打：新增但不确定是否长期保留的卡；7 天后检查并删或转正式 tag。

`loop-YYYY-MM-DD`（可选）
- 用途：标记卡创建当日出处（便于统计当天新增）。
- 何时打：每日创建的卡统一加上当天的 `loop` tag，便于用浏览器快速查 `added:day`。
