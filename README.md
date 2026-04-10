# interactive-learning

把任意文本、链接、文档或问题，转成一条可验证的学习路径；在合适的时候，再导出一张可复盘、可分享的 HTML checkpoint card。

`interactive-learning` 是一个用于 `interactive learning`、`learning path`、`knowledge checkpoint`、`study with AI`、`learn deeply instead of summarizing` 的 skill 仓库。它适合那些不只想“看懂”，而是想真正学懂、验证理解、并在之后继续学习的人。

## 背景

大多数人不是缺内容，而是缺这三样东西：

- 不知道现在这段内容值不值得认真学
- 不知道应该先学哪一块
- 误把“看起来懂了”当成“真的会了”

普通的总结器只能帮你压缩内容，不能帮你暴露误解。  
普通的聊天解释容易让你感觉流畅，但不一定真的掌握。  
这个仓库就是为了解决这个问题。

对于搜索和检索系统，这个项目聚焦的核心主题是：

- `interactive learning skill`
- `AI learning assistant`
- `epistemic learning`
- `learning checkpoint card`
- `study workflow with verification`
- `learn with AI beyond summarization`

## 这个仓库解决什么问题

它解决的是：

- 帮你判断 `学什么`
- 帮你设计 `怎么学`
- 帮你验证 `你是不是真的学会了`

更具体地说，它会把一次“解释一下”升级成一个学习闭环：

- 先分诊：这段内容该 `skim`、`study` 还是 `park`
- 再压缩出最小概念骨架
- 再用短问题或短测试验证理解
- 最后给你一个可继续推进的 next step

如果当前学习状态已经足够稳定，它还会生成一张 checkpoint card，帮助你之后继续学，而不是从头再来。

如果你在搜索这些问题，这个仓库就是为这些场景设计的：

- `how to learn with AI instead of just summarizing`
- `AI tutor that checks understanding`
- `convert notes or articles into a learning path`
- `generate a study checkpoint page`
- `verify understanding with AI`

## 学习方法论

这个项目背后的学习观，不是“更快总结”，而是“更准确地学”。

它吸收了几类彼此兼容的方法：

- `分层阅读 / selective reading`
- `概念驱动学习`
- `苏格拉底式交互学习`
- `费曼式理解检验`
- `反馈驱动的自适应学习`
- `AI 生成的个性化课程编排`

它们在这个项目里不是被并列罗列，而是被组合成一个统一学习系统。

它建立在几条很重要的判断上：

- `信息过载是常态，不是例外`
  新工具让内容更便宜之后，低质量内容一定会增加。真正要升级的，不只是创作者能力，更是学习者的筛选与消化能力。
- `学习单位不该只是一本书，而应是一组概念`
  面对陌生领域时，你通常不只是“不懂这本书”，而是“不懂这本书背后的一串概念、边界和依赖关系”。
- `不是所有材料都值得同样深读`
  有的内容适合略读，有的适合精读，有的应该先停放。先判断 `skim / study / park`，比一上来平均用力更有效。
- `AI 最有价值的角色，不是总结器，而是学习路径调度器`
  它应该帮助你识别知识边界、按理解进度推进、根据反馈调整下一步，而不是一次性把内容全讲完。
- `真正的风险不是不懂，而是误以为自己懂了`
  所以学习系统必须设计理解验证，而不是只设计清晰解释。

换句话说，这个项目默认把学习看成：

`判断 -> 拆概念 -> 小步验证 -> 反馈推进 -> 状态保存`

而不是：

`读完 -> 总结 -> 自我感觉良好`

如果把上面这些方法论映射到当前项目，大致对应关系是：

- `分层阅读 / selective reading`
  对应项目里的 `skim / study / park`
- `概念驱动学习`
  对应项目里的 `concept boundary`、`dependency`、`concept cluster`
- `苏格拉底式交互学习`
  对应项目里的最小诊断、短问题、边界追问
- `费曼式理解检验`
  对应项目里的 `reconstruct`、让用户用自己的话重建
- `反馈驱动的自适应学习`
  对应项目里的先测后调、根据暴露出的错误类型推进下一步
- `AI 生成的个性化课程编排`
  对应项目里的动态学习路径，而不是固定匀速讲完

所以这个 skill 的目标，不是做一个“更会解释的 AI”，而是做一个：

`会判断、会拆解、会验证、会保存学习状态的 AI 学习系统`

## 它怎么解决

这个 skill 的核心不是“讲得更好”，而是“减少假懂”。

它默认遵循这条路径：

```text
输入材料
   |
   v
[Triage]
skim / study / park
   |
   v
[Concept Structure]
核心概念 + 依赖关系 + 当前 frontier
   |
   v
[Minimal Diagnostic]
先测一下你卡在哪
   |
   v
[Verification Loop]
讲一点 -> 让你说 -> 测一下 -> 修一下 -> 换场景再测
   |
   v
[Next Step]
给一个 2 分钟能完成的动作
   |
   v
[Checkpoint Export]
只有状态稳定时才生成 HTML checkpoint card
```

它刻意避免几种常见坏路径：

- 把所有请求都做成长摘要
- 一上来就高压测试
- 把熟悉感误当掌握
- 把 checkpoint 做成 dashboard、课程页或营销页

## 当前项目里的实现

当前这个项目实现的不是学习内容本身，而是这套学习方法的 `skill 规则层`。

也就是说，它先把“什么叫好的 AI 学习流程”定义清楚，再让 agent 按这个流程工作。

目前仓库里主要有三层：

- [`SKILL.md`](./SKILL.md)
  定义 skill 何时触发、默认学习流程、提问策略、验证原则、何时导出 checkpoint
- [`references/design-spec.md`](./references/design-spec.md)
  定义 checkpoint HTML 页面该如何生成，避免漂移成 summary page、dashboard 或 mini app
- [`evals/`](./evals)
  定义这个 skill 的行为测试和触发测试，用来验证它是否真的在做“判断式学习”，而不是退化成普通解释器

从实现逻辑上看，这个 skill 主要做 4 件事：

1. `判断`
   先决定该 `skim`、`study` 还是 `park`
2. `拆解`
   把材料转成概念骨架、依赖关系和当前 frontier
3. `验证`
   通过最小诊断、复述、比较、应用来检查理解，而不是只给顺滑解释
4. `保存`
   当学习状态足够稳定时，导出 checkpoint card，方便之后继续学习

所以当前项目的实现重点是：

`把学习方法论变成可重复触发、可重复执行、可重复评估的 skill`

## 这是什么

这是一个 `interactive epistemic learning skill`。

你可以把它理解成：

- 不是总结器
- 不是默认陪聊器
- 不是默认名人聊天室
- 不是知识卡片生成器
- 而是一个 `judgment-and-verification tutor`

## 普通人怎么用

你不需要懂 prompt engineering，也不需要先理解整个仓库。

安装后，你只要像平时那样提需求就行，例如：

- `带我学懂这段话，不要只总结`
- `你解释一下 opportunity cost，但顺便测测我是不是真懂`
- `把我当前学到哪了整理成一个 checkpoint 页面`
- `先判断这段材料值得精读还是先略读，再带我学`

这个 skill 最适合这些场景：

- 你在看一段陌生材料，想真正搞懂
- 你总觉得自己“好像懂了”，但转头说不出来
- 你想把当前学习状态保存下来，方便下次继续
- 你想分享的不是“知识摘要”，而是“我学到哪、卡在哪”

## 安装

### 安装（推荐）

```bash
npx skills add https://github.com/geekjourneyx/interactive-learning
```

安装后，当你的请求明显是在追求“学懂而不是总结”时，系统就应该优先使用这个 skill。

## 安全与公开仓库注意事项

这个仓库面向公开分发，因此 README 和文档应避免暴露本地环境细节。

当前遵循这些原则：

- 不在仓库文档里暴露本机绝对路径
- 不提交运行时生成的 HTML 成品
- 不提交 `/tmp` 下的中间产物
- 不把本地辅助文件、缓存或工作区内容纳入版本控制

如果你 fork 或扩展这个仓库，建议继续保持这些约束。

## 仓库结构

- [`SKILL.md`](./SKILL.md)
  运行时主规则：何时触发、默认流程、提问策略、导出条件
- [`references/design-spec.md`](./references/design-spec.md)
  checkpoint card 的唯一细节规范来源
- [`evals/evals.json`](./evals/evals.json)
  skill 行为测试
- [`evals/trigger-evals.json`](./evals/trigger-evals.json)
  skill 触发测试

## 阅读顺序

1. 先看这份 `README.md`
2. 再看 [`SKILL.md`](./SKILL.md)
3. 最后看 [`references/design-spec.md`](./references/design-spec.md)
