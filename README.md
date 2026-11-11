# 自媒体文案优化器（media-copy-optimizer）

一句话定位：把客户发来的文案，改写成能留住观众的视频口播稿和可直接发布的图文逐字稿。

An Agent Skill that turns a client's raw copy into a retention-oriented short-video voiceover script and a publish-ready image-text script, with titles, cover copy, and publishing notes.

## 简介

这是一个面向自媒体从业者、代运营团队和企业市场人员的 Agent Skill。客户发来一段文案、卖点、草稿或长文后，它会先拆解受众、目的与核心主张，再选择一个明确的流量角度，输出一篇按时间轴组织的视频口播稿，以及一篇包含标题、封面、正文、标签的图文逐字稿。它强调开头留人、中段有信息增量、结尾有行动，同时坚持不改变事实、不编造数据、不承诺流量结果。

This skill is built for creators, agencies, and in-house marketing teams. Given a client's draft, it identifies the audience, goal, and single core message, chooses one traffic angle, and produces a timestamped video voiceover script plus a ready-to-publish image-text script with titles, cover copy, body text, and hashtags. It prioritizes retention and clarity while refusing to fabricate facts, metrics, or guaranteed reach.

## 运行示例

输入：

```text
我们店新出了一款低糖蛋糕，用的是赤藓糖醇，适合控糖的人，口感也不差，欢迎来买。
```

输出结构（节选）：

```text
【内容判断】受众：控糖人群；目的：到店尝试；主角度：想吃又不敢吃；建议时长：60 秒

【标题候选】
1. 控糖也能吃蛋糕，我把糖换成了它
2. 控糖以后，我终于敢买生日蛋糕了
……

【视频口播稿】（约 60 秒，240 字）
[0 至 3 秒] 控糖以后，你是不是连生日蛋糕都不敢碰了？
[3 至 10 秒] 不是不想吃，是配料表一翻，糖、奶油、面粉，全在劝退。
……

【图文逐字稿】
标题：控糖也能吃蛋糕，我把糖换成了它
封面：主标题「控糖也能吃蛋糕」／副标题「这次我把糖换成了赤藓糖醇」
正文：……
标签：控糖饮食、低糖蛋糕、……

【假设与待补充】价格、门店地址、检测报告未提供，已在成稿中标注【待补充：……】
```

## 安装方式

Skill 是一个文件夹，不是安装程序。把整个 `media-copy-optimizer` 目录复制到对应客户端的 skills 目录，重启客户端或在客户端中执行 skills 重载即可。

- WorkBuddy 用户级：`~/.workbuddy/skills/media-copy-optimizer/`
- WorkBuddy 项目级（团队共享）：项目根目录 `.workbuddy/skills/media-copy-optimizer/`
- Qoder 用户级：`~/.qoder/skills/media-copy-optimizer/`
- Qoder 项目级：项目根目录 `.qoder/skills/media-copy-optimizer/`
- Claude Code 用户级：`~/.claude/skills/media-copy-optimizer/`
- Claude Code 项目级：项目根目录 `.claude/skills/media-copy-optimizer/`

其他兼容 Agent Skills 规范的客户端，通常读取 `~/.<client>/skills/` 或项目内 `.<client>/skills/`，具体以客户端文档为准。

安装后确认目录结构如下，`SKILL.md` 必须直接位于 `media-copy-optimizer/` 下：

```text
media-copy-optimizer/
├── SKILL.md
├── references/
└── assets/
```

## 使用方法

直接用自然语言发送文案，并说明想要的稿型、平台或时长。示例：

1. “帮我把这段产品介绍改成抖音口播稿，60 秒，开头要抓人。”
2. “这是我们门店的活动文案，写一版小红书图文逐字稿，语气真诚一点，不要像广告。”
3. “这篇公众号太书面了，改成视频号口播稿，保留原来的数据。”
4. “客户给了这段卖点，帮我出两个版本：一个稳妥，一个强钩子。”
5. “只要图文稿，标题给 5 个，正文控制在 600 字以内。”

未指定平台时输出通用版；未指定时长时，口播默认 60 至 90 秒，图文默认 400 至 800 字。

## 工作方式

1. 拆解原文：受众、目的、核心主张、素材、语气、平台、时长。
2. 选择一个流量角度：反常识、结果先行、代价、身份共鸣、对比或清单。
3. 写 3 秒钩子，并准备备选钩子。
4. 按内容类型写视频口播稿，每 10 至 15 秒设置一个留存点。
5. 写图文逐字稿：5 个标题、封面文案、短段落正文、标签。
6. 做事实、节奏、平台与合规检查，再按固定格式交付。

## 目录结构

```text
media-copy-optimizer/
├── SKILL.md                              # 核心流程与输出规范
├── README.md                             # 项目说明
├── LICENSE                               # MIT
├── .gitignore
├── CHANGELOG.md
├── references/
│   ├── hook-library.md                   # 开头钩子、中段留存点与反例
│   ├── script-structures.md              # 视频与图文结构、节奏、改写对照
│   ├── platform-playbook.md              # 抖音、小红书、视频号等平台适配
│   └── quality-and-compliance.md         # 交付检查与合规边界
└── assets/
    ├── video-script-template.md          # 口播稿输出模板
    └── image-text-template.md            # 图文逐字稿输出模板
```

## 设计原则

- 只选一个主角度：一条内容解决一个问题。
- 开头先给“与我有关”的冲突或结果，不做自我介绍式铺垫。
- 具体优先：场景、动作、数字、对比，但不得虚构。
- 口语优先：短句、少术语、可朗读。
- 事实优先：原文没有的数据、案例、资质不补造，缺失用【待补充：……】标出。
- 合规优先：不使用绝对化用语和无法兑现的效果承诺。
- 不承诺流量：只提供高留存写法与可测试变量，不保证播放、涨粉或转化。

## 常见问题

**安装后没有触发怎么办？**

先确认 `SKILL.md` 是否直接位于 `media-copy-optimizer/` 目录下，文件夹名是否与 frontmatter 的 `name` 完全一致；再检查 frontmatter 是否为合法 YAML、文件是否为 UTF-8 编码；最后重启客户端或执行 skills 重载。若仍不触发，在请求中直接写出“使用 media-copy-optimizer”或点名“口播稿、图文逐字稿”。

**为什么没有直接给我“爆款”？**

流量受选题、账号权重、画面、发布时间等多种因素影响，任何单一文案都无法保证结果。本 Skill 优化的是开头留存、信息密度和行动设计，并给出可测试变量。

**原文信息太少怎么办？**

会先基于现有信息产出最短可用版本，并用【待补充：……】标出缺口；只有缺失信息会实质改变结论时，才会追问一个合并问题。

**可以只输出口播稿或只输出图文稿吗？**

可以。明确说明即可，但仍会附上标题候选与自检说明。

**能指定平台、时长、禁用词吗？**

可以。平台、时长、语气、禁用词和必须保留的原话都会被优先遵守。

**会不会把我的原文改得面目全非？**

不会。核心主张和事实保持不变，改动集中在信息顺序、表达方式、节奏和行动设计；涉及夸大的部分会降级为可证实说法，并说明原因。

## 许可证与致谢

MIT License，见 [LICENSE](LICENSE)。基于 Agent Skills 开放规范构建，兼容 WorkBuddy、Qoder、Claude Code 等支持该规范的客户端。

## 仓库信息

建议仓库描述：把客户文案改写成高留存视频口播稿与图文逐字稿的 Agent Skill。

建议 GitHub Topics：

`agent-skills` `ai` `copywriting` `content-marketing` `short-video` `xiaohongshu` `script-writing` `prompt-engineering`

本仓库不提供编译好的 exe/msi 安装包，Release 中的 Source code 是源码快照。
