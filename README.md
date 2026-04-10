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
