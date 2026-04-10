# interactive-learning

把任意文本、链接、文档或问题，转成一条可验证的学习路径；在合适的时候，再导出一张可复盘、可分享的 HTML checkpoint card。

`interactive-learning` 是一个面向 `interactive learning`、`learning path`、`knowledge checkpoint`、`study with AI` 的 skill 仓库。适合想真正学懂、验证理解、继续推进的人。

## 安装

```bash
npx skills add https://github.com/geekjourneyx/interactive-learning
```

安装后，下面这类请求会优先触发这个 skill：

- `带我学懂这段话，不要只总结`
- `你解释一下 opportunity cost，但顺便测测我是不是真懂`
- `把我当前学到哪了整理成一个 checkpoint 页面`
- `先判断这段材料值得精读还是先略读，再带我学`

## 背景

多数人缺的不是内容，缺的是学习判断：

- 不知道现在这段内容值不值得认真学
- 不知道应该先学哪一块
- 误把“看起来懂了”当成“真的会了”

总结器解决压缩，解决不了误解。  
聊天解释解决流畅，解决不了掌握。  
这个仓库补的是这块。

## 这个仓库解决什么问题

核心作用有三件：

- 帮你判断 `学什么`
- 帮你设计 `怎么学`
- 帮你验证 `你是不是真的学会了`

一次“解释一下”，在这里会被升级成一个学习闭环：

- 先分诊：这段内容该 `skim`、`study` 还是 `park`
- 再压缩出最小概念骨架
- 再用短问题或短测试验证理解
- 最后给你一个可继续推进的 next step

学习状态足够稳定时，还会生成一张 checkpoint card，方便下次继续，而不用从头来。

## 学习方法论

- `分层阅读 / selective reading`
- `概念驱动学习`
- `苏格拉底式交互学习`
- `费曼式理解检验`
- `反馈驱动的自适应学习`
- `AI 生成的个性化课程编排`

对应到项目里，是几条简单判断：

- `信息过载是常态`
  新工具让内容更便宜后，低质量内容一定增加。学习者的筛选和消化能力更重要。
- `学习单位更接近一组概念`
  难点通常不止在一本书，而在书背后的概念、边界和依赖。
- `不同材料需要不同深度`
  有的略读，有的精读，有的先停放。先判断 `skim / study / park` 更有效。
- `AI 更适合做学习路径调度`
  AI 可以识别知识边界、按理解进度推进、根据反馈调整下一步。
- `最大的风险是误以为自己懂了`
  所以系统必须设计理解验证。

默认学习路径是：

`判断 -> 拆概念 -> 小步验证 -> 反馈推进 -> 状态保存`

## 它怎么解决

重点是减少“假懂”。

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

当前仓库实现的是这套学习方法的 `skill 规则层`。

目前仓库里主要有三层：

- [`SKILL.md`](./SKILL.md)
  定义 skill 何时触发、默认学习流程、提问策略、验证原则、何时导出 checkpoint
- [`references/design-spec.md`](./references/design-spec.md)
  定义 checkpoint HTML 页面该如何生成，避免漂移成 summary page、dashboard 或 mini app
- [`evals/`](./evals)
  定义这个 skill 的行为测试和触发测试，用来验证它是否真的在做“判断式学习”，避免退化成普通解释器

运行时主要做 4 件事：

1. `判断`
   先决定该 `skim`、`study` 还是 `park`
2. `拆解`
   把材料转成概念骨架、依赖关系和当前 frontier
3. `验证`
   通过最小诊断、复述、比较、应用来检查理解，不停留在顺滑解释
4. `保存`
   当学习状态足够稳定时，导出 checkpoint card，方便之后继续学习

## 这是什么

这是一个 `interactive epistemic learning skill`，也是一个 `judgment-and-verification tutor`。

## 普通人怎么用

适合这些场景：

- 你在看一段陌生材料，想真正搞懂
- 你总觉得自己“好像懂了”，但转头说不出来
- 你想把当前学习状态保存下来，方便下次继续
- 你想分享的是“我学到哪、卡在哪”

## 安全与公开仓库注意事项

这是公开仓库，文档需要避免暴露本地环境细节。

- 不在仓库文档里暴露本机绝对路径
- 不提交运行时生成的 HTML 成品
- 不提交 `/tmp` 下的中间产物
- 不把本地辅助文件、缓存或工作区内容纳入版本控制

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
