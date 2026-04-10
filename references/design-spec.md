# Interactive Learning Checkpoint Card Design Spec

这是 checkpoint card 的唯一细节规范来源。  
它定义：

- 页面定位
- 信息架构
- 数据契约
- 视觉系统
- 交互系统
- 禁止项与验收标准

它不是静态页面源码，不承担仓库内展示功能。

## 页面定位

页面名称固定为：

- `Learning Checkpoint Card`

页面的真正任务是回答四件事：

1. 你现在在学什么
2. 哪几个概念最关键
3. 你卡在哪
4. 你下一步该干嘛

页面只承担三个任务：

- `resume`
- `retrieve`
- `share state`

## 信息架构

动态生成页面必须按以下顺序组织，不能扩成多面板应用：

1. `Header`
   - Topic title
   - 一句话 `topic_frame`
   - 分享按钮

2. `Concept Spine`
   - 3-7 个节点
   - 使用 `dependency ladder` 或极简 `node chain`
   - 不使用大图谱

3. `Current Frontier`
   - 当前 unresolved confusion
   - 页面需要保留一种“尚未完成”的感觉

4. `Active Prompt`
   - 页面唯一主交互区
   - 默认一个 `reconstruct` prompt
   - 先尝试，再 reveal

5. `Next Step`
   - 只给一个 2 分钟动作
   - 只能有一个

6. `Source Anchor`
   - 一个回源入口
   - 视觉弱化，不抢主任务

## 数据契约

运行时动态页面至少需要以下字段：

- `topic_frame`
- `concept_spine`
- `frontier`
- `active_prompt`
- `next_step`
- `source_anchor`
- `share_meta`

建议结构：

```json
{
  "topic_frame": {
    "title": "string",
    "summary": "string"
  },
  "concept_spine": [
    {
      "label": "string",
      "status": "clear|shaky|untested",
      "hint": "string",
      "note": "string"
    }
  ],
  "frontier": {
    "question": "string",
    "why_it_matters": "string"
  },
  "active_prompt": {
    "type": "reconstruct",
    "question": "string",
    "reveal_hint": "string",
    "secondary_transfer_hint": "string"
  },
  "next_step": {
    "duration": "2 minutes",
    "action": "string"
  },
  "source_anchor": {
    "label": "string",
    "href": "string"
  },
  "share_meta": {
    "slug": "string",
    "generated_at": "ISO-8601 string"
  }
}
```

说明：

- `status` 是概念节点上的粗粒度状态，不需要单独再建 `status_markers`
- `frontier` 必填，因为页面必须明确当前卡点
- `share_meta` 只服务分享和运行时管理，不参与主内容表达
- `active_prompt` 应优先测试 `frontier` 指向的真实区别，不能只是泛泛复述题

## 视觉系统

- 安静
- 克制
- 可信
- 非营销页
- 非产品发布页

参考逻辑：

- 内容边界和秩序感像 Vercel / Notion
- 阅读节奏和温度感像 Claude
- 反模板化要求对齐 taste-skill

默认走低饱和、纸感、轻对比路线。

不允许：

- 过亮主色
- UI 仪表盘式蓝紫荧光
- 社交产品式高刺激色
- 黑底霓虹感

排版约束：

- 单栏优先
- 标题强调信息，不强调英雄感
- 正文必须短
- 标签必须克制
- 大部分页面高度应适配手机一屏半到两屏，不追求长滚动

允许：

- 小型依赖链 / 梯子
- 状态 pill
- 一个主 prompt 区
- 一个 next-step box

不允许：

- chart-heavy layout
- 多 panel
- tab system
- chat shell
- persona cards
- carousel

## 交互系统

允许的交互：

- 点击节点查看极简说明
- `Try first / Reveal`
- 标记状态：`clear / shaky / untested`
- 一键分享

禁止的交互：

- 多题切换
- 多轮问答
- 聊天输入框
- 节点拖拽
- 大图谱漫游
- 复杂筛选
- 模式切换器

页面永远只有一个主测试动作。

`transfer` 可以保留为次级提示或 next step，但不能和 `reconstruct` 并列成为第二主 CTA。

状态只允许粗粒度表达：

- `clear`
- `shaky`
- `untested`

不允许：

- 每节点百分比分数
- 精细 mastery score
- 自动生成“完成度 xx%”
- 任何暗示“系统已经精确评估你掌握程度”的表达

## 禁止项

以下任一出现，都说明设计偏了：

- 长摘要
- 大段正文
- 进度条
- gamification
- persona 可视化
- 大知识图谱
- 多个并列测试入口
- dashboard 感
- 小型课程页
- “完成度 xx%”
- 页面看起来像作品集切片

## 运行时输出约束

仓库内不提交固定 HTML 成品。  
所有页面必须由 agent 在运行时根据内容动态生成。

建议输出路径：

```text
/tmp/interactive-learning-checkpoint-[slug].html
```

如果没有形成稳定 checkpoint，不生成页面。

## 验收标准

- 5 秒内看懂“在学什么 / 卡在哪 / 下一步干嘛”
- 主要促进回忆，而不是阅读
- 能帮助用户在中断后重新进入学习
- 对外分享时，能传达学习状态，而不是只传达审美

## 失败信号

- 用户主要滚动阅读，不主动作答
- 用户把拥有页面当成完成学习
- 页面逐步长成 mini app
- 页面被当成营销物料而不是 checkpoint
