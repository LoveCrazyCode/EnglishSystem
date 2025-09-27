# anki 复习与跟踪策略（结合本学习系统）

> 目标：最小投入（每日 ≤5 分钟维护 Anki），最大化 “升级句 / 最难 chunk / 迁移原则” 的长期保持，不把 Anki 变成堆积任务。

## 1. 核心理念（只记这 5 条）
1. 卡片数量越少越好：每日新增 ≤3（升级 / 最难 / 迁移）。
2. 只做“复用价值 + 难再生”内容的卡片（轻易可再造的句子不要卡片化）。
3. 升级句 > 原始句；优先记“新表达方式”而不是“生词拼写”。
4. 迁移结构（principle → domain → result）必须定期被迫回想，否则会回落成单一场景表达。
5. Anki 是补强，不是主循环；10 分钟主循环优先，卡片是最后 1–2 分钟。

## 2. Deck / Tag 结构（推荐）
采用“单 Deck + 标签”方式，避免跨 Deck 调度复杂。

Deck: `EnglishActive`  （所有卡片都放这里）

Tags（按功能分类，可多标签）：
- `chunk`：固定短语 / collocation（如 roll clothes to save space）
- `function`：功能表达骨架（like I’d rather sacrifice X…）
- `upgrade`：旧→新后的新句（重点）
- `transfer`：迁移原则句
- `skeleton`：P-R-E / P-R-E-C-W 骨架提示（少量）
- `ladder`：表达升级阶梯（可选）
- `temp`：候选，7 天后决定留/删

日期 Tag（自动追踪来源）：`loop-2025-09-27`（当天创建的所有卡，加一个）

## 3. Note 类型与模板（最少 2 种）
### a. Cloze（主力）
字段：`Text` / `Extra`
用法：保留自然句子 → 去掉最核心 1–2 位置。
示例：My rule of {{c1::thumb}} is to pack {{c2::versatile}} items.

### b. Speaking Prompt（输出/迁移）
字段：`Prompt` / `Hint` / `Target`
Front 显示：Prompt（如：Explain one packing change + result）
Back：示例骨架 + 参考升级句
口头说完再翻面；自评（✓ / ✗）不必打字。

（可选）Transformation Note（Basic 型）：Front 放基础句，Back 放升级思路 + 目标版本；用来刻意练“提升”。

## 4. 每日 10 分钟循环 → Anki 映射
| 循环动作 | 是否必建卡 | 卡片类型 | 数量上限 |
|----------|-----------|----------|----------|
| 选 5 语块 | 否（除非极难记） | Cloze (chunk) | 0–1 |
| 骨架输出 | 否（骨架在脑中复现即可） | Skeleton (可选) | 0 |
| 升级 1 句 | 是（核心） | Cloze (upgrade) | 1 |
| 迁移 1 句 | 建议 | Speaking Prompt / Cloze | 1 |
| 录音回听标 2 处 | 视情况 | 若出现“新结构”可卡 | 0–1 |
| 制卡 | 严格 ≤3 | 上述 | ≤3 |

## 5. 创建决策树
```
这条内容是否：
  A. 跨 ≥2 场景可复用？ → 是 → 可做卡
  B. 没卡住就能再说出？ → 是 → 不做卡
  C. 升级句提升显著（机制/度量/对比）？ → 是 → 做卡
  D. 迁移句结构未来想自动化？ → 是 → 做卡
 其他 → 放弃
```

## 6. Anki 调度设置（建议参数）
在 Deck 选项中：
- New cards / day：6（但你实际只用 ≤3）
- Bury siblings：开启（避免同一句多个 cloze 连续出现）
- Graduating interval：3 天（默认 1 → 3 提升复现效率）
- Easy interval：5 天（避免过早膨胀）
- Maximum interval：90 天（现阶段不追求年级别）
- Minimum ease：不要低于 130%（低于则说明卡片设计太机械，应合并或删除）

手机上若复习压力 > 30 张 / 天：
1) 检查是不是做卡太多  2) 删除 `temp` 标记后 7 天表现良好但“无复用”的。

## 7. 迁移 / 升级 专用 Tag 复盘
每周（周末 2 分钟）：
1. 在浏览器搜索 tag:`upgrade` prop:due<=1d → 查看仍会错的表达；必要时重新口头复述。
2. 搜索 tag:`transfer`，点“统计”看易错集中在哪类结构（if / principle / trade-off）。
3. 挑 1 条重复出错的迁移句写“第二次升级版”（再度精炼）。

## 8. progress_log 联动
日志字段与 Anki 对应：
| progress_log 列 | 生成方式 |
|-----------------|----------|
| new expressions | 当天卡片数（不含 speaking prompt）或 5 语块里真正“全新”的数 |
| upgrades | 当天 tag:upgrade 新增数 |
| transfers | 当天 tag:transfer 新增数 |
| recordings | 保持 1×40s（与 Anki 无关） |
| self-score | 回忆流畅度主观 1–5 |

快速统计（桌面 Anki 浏览器搜索）：
- `added:1` （当天）+ 过滤 `tag:upgrade` → 升级计数
- `added:1 tag:transfer` → 迁移计数

## 9. 删除 / 合并策略
| 问题 | 判断 | 动作 |
|------|------|------|
| 卡片重复 | 同一句两个 cloze 间隔极短 | 合并成一个，保留最难空位 |
| 永远 easy | 连续 3 次 “Easy” | 删除（已内化）|
| 总是 again | 连续 3 次 <10s 回答错误 | 重写句子（可能信息量过大）|
| 冷僵公式化 | 读起来不自然 | 改为更口语 / 分两张 |

## 10. 示例（真实一组）
原句：I bring fewer things.  → 升级：I strip out single‑purpose items so my bag stays lightweight.
Cloze：I strip out {{c1::single‑purpose}} items so my bag stays {{c2::lightweight}}.

迁移句：I strip out single‑purpose items → I strip out single-purpose calendar blocks so the week stays flexible.
Speaking Prompt：Explain how your packing changed and what principle guides it now.

Transformation 卡：
Front：Basic: I bring fewer things.
Back：Add mechanism + result → I strip out single-purpose items so my bag stays lightweight.

## 11. 3 分钟极简日（只保留复现）
若时间极少：只做当天 due 的 tag:upgrade；忽略 chunk（chunk 可通过口头复述补）。

## 12. 与系统其它文件的连接
- `guides/daily-loop-mobile.md`：告诉你什么时候“制卡”。
- `topics/<topic>.md`：永远是卡片来源（原始升级/迁移写在文件→再卡片）。
- `logs/progress_log.md`：不记录“复习结果”，只记录“是否新增 + 是否升级 + 是否迁移”。

## 13. 常见误区与纠偏
| 误区 | 迹象 | 调整 |
|------|------|------|
| 建太多 | 新卡>5 | 强制限 3，删 temp |
| 只记词不记结构 | 卡全是名词短语 | 每天 ≥1 条 upgrade 或 transfer |
| 忽略听说复现 | 只点背卡 | 录音优先，卡片是附加 |
| 升级句很容易 | 几乎不出错 | 提升到加机制/度量/对比再做卡 |
| 迁移卡难想 | 放弃卡片 | 先卡“套壳模板” (I apply the same principle to…) |

## 14. FAQ
Q: 需要给骨架做卡吗？  A: 不需要，P-R-E 频繁口头使用即可。 
Q: Cloze 要不要一次挖 3 个空？ A: 1–2 个足够；3 个增加失败率且降低复现愉悦度。
Q: 升级句是否保留旧句？ A: 旧句不做卡（写在主题文件对照即可）。

## 15. 建议启动步骤（首次 5 分钟）
1. 新建 Deck `EnglishActive`。
2. 选出最近 2 天最典型的 2 升级句 + 1 迁移句建 3 张卡（打 tag：upgrade / transfer + loop-日期）。
3. 调整 Deck 选项（Graduating=3d, Easy=5d, New/day=6）。
4. 设手机小组件/快捷方式直达“添加牌”界面。
5. 明天开始按循环每日 ≤3 张。

> 质重于量：如果今天没有值得做卡的升级句，就不建；空缺比垃圾卡更健康。

---
## 附：stub（占位文件）是什么意思？
“stub” 在你的清理计划里指：
1. 一个已迁移内容后的“占位/提示”文件。
2. 只含几行：告知新位置 + 过期删除日期。
3. 目的：避免外部/旧书签 404，给你迁移缓冲期。
4. 到期（如 2025-10-05）后可以安全删除，不再维护其中内容。

好处：
- 明确哪些文件是“临时兼容层”
- 防止误编辑旧副本
- 给清理设定明确时间点

使用建议：在 README 或 `bk/README.md` 标注统一删除日，一次性清理。

---
需要进一步：如果你想要“具体 Anki NoteType 字段与模板 HTML” 或 “iOS 快捷指令脚本说明”，告诉我，我再补充。 