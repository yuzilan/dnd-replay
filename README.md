# dnd-replay

`dnd-replay` 是一个面向 Codex 的 D&D TRPG 跑团战报整理 Skill。它把跑团转写、聊天记录、战斗日志和角色资料重建为每回战报，并在长模组中持续维护人物、NPC、物品、线索、谜团和任务状态。

它的原则是：**忠实记录玩家真正经历过的冒险，不替玩家补写一个“看起来合理”的故事。**

## 能做什么

- 从腾讯会议、Zoom、Discord、QQ 等来源的文字转写重建一回冒险。
- 处理已区分说话人、只有“说话人 1/2/3”或全部混成一个说话人的转写。
- 按实际玩家角色数量整理角色行动，不预设 4 人、6 人或任何固定人数。
- 整理剧情、战斗、装备、金钱、NPC 关系、线索、谜团和名场面。
- 为长模组维护 Campaign Profile、每回战报和 Campaign Ledger。
- 检查 NPC 生死、物品归属、角色状态、地点和线索的前后连续性。
- 回答“这件物品从哪里来”“某 NPC 第一次何时出现”等历史问题。

它不会：

- 把模组原文当作玩家已经经历的剧情；
- 编造缺失的说话人、骰点、战斗结果、谜题答案或物品归属；
- 用 D&D 标准规则覆盖本团实际采用的 DM 判定。

## 仓库文件说明

| 文件 | 用途 |
| --- | --- |
| `SKILL.md` | Codex 使用的核心工作规则、事实优先级和任务路由。 |
| `references/campaign-state.md` | Campaign Profile、档案目录和长期 Campaign Ledger 的格式及更新规则。 |
| `references/transcript-analysis.md` | 转写类型、说话人识别、事实等级、战斗重建和纠错规则。 |
| `references/chronicle-style.md` | 场景切分、叙事节奏、台词、角色高光和结语的写作标准。 |
| `references/output-formats.md` | Markdown、Word、PDF、TXT 和多格式交付的询问、生成与验证规则。 |
| `references/report-format.md` | 每回战报固定八个栏目及回末队伍状态格式。 |
| `agents/openai.yaml` | Codex 界面显示名称、简短介绍和默认调用提示。 |
| `README.md` | 面向使用者和 GitHub 访客的安装、准备资料与使用说明。 |

## 安装

### 方式一：使用 `$skill-installer` 从 GitHub 安装

用户可以在 Codex 中发送：

```text
$skill-installer 从 GitHub 仓库 https://github.com/yuzilan/dnd-replay 安装根目录的 Skill，名称设为 dnd-replay。
```

安装器会把它安装到个人 Codex Skills 目录。安装完成后，在下一轮对话或新的 Codex 任务中使用 `$dnd-replay`。

### 方式二：手动 clone

```bash
git clone https://github.com/yuzilan/dnd-replay.git ~/.codex/skills/dnd-replay
```

也可以下载 ZIP 后解压到 `~/.codex/skills/dnd-replay`。无论使用哪种方式，都应确保目录结构如下：

```text
~/.codex/skills/dnd-replay/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── campaign-state.md
    ├── chronicle-style.md
    ├── output-formats.md
    ├── report-format.md
    └── transcript-analysis.md
```

如果该路径已经存在，请先备份或换一个 Skill 名称，不要直接覆盖尚未确认的个人修改。安装后，在新的 Codex 任务中使用 `$dnd-replay` 明确调用。

## 需要准备或上传什么

### 最低资料

第一次整理某个 Campaign，至少准备：

1. Campaign 或模组名称。
2. 长模组、短模组还是单回冒险。
3. 当前是第几回、第几幕或第几章。
4. 实际玩家角色名单，至少包含“玩家名｜角色名”；种族、职业、等级等已知多少写多少。
5. 本回的文字转写、聊天记录或玩家笔记。
6. 希望收到的战报格式：对话、Markdown、Word、PDF、TXT 或多格式。

### 推荐补充资料

- 模组简介：只作为背景，不会自动写成玩家经历。
- “说话人 → 玩家/角色”对应表。
- 角色卡或角色信息表。
- 战斗日志、骰点记录或 VTT 导出。
- DM 笔记、玩家笔记和文字聊天记录。
- 已有的前回战报或 Campaign Ledger。
- 已确认的 NPC、地点、法术、怪物和物品正确写法。

### 常见文件形式

优先使用可检索文字，例如 `.txt`、`.md`、会议转写、Discord 聊天导出或 VTT 日志。也可以提供包含文字的 `.docx`、`.pdf` 或清晰图片，但复杂排版和手写内容可能需要额外确认。

这个 Skill 本身不是语音转写工具。如果只有音频，建议先生成文字转写，再将转写交给 `$dnd-replay`。

### 选择战报输出格式

如果用户没有指定，Skill 会在首次制作文件前询问：

> 你希望战报输出为 Markdown (`.md`)、Word (`.docx`)、PDF (`.pdf`)、纯文本 (`.txt`)，还是同时输出多种格式？这是长模组的话，是否同时保留 Markdown 作为后续持续更新的主档？

| 格式 | 适合用途 | 说明 |
| --- | --- | --- |
| Markdown | 长期维护、GitHub、继续交给 Codex 更新 | 长模组推荐作为主档 |
| Word | 人工编辑、批注、分享 | 使用标题、表格、分页等 Word 版式 |
| PDF | 阅读、打印、固定版式发布 | 生成后需要逐页检查排版 |
| TXT | 兼容性最高、纯文本存档 | 不依赖 Markdown 表格和样式 |
| 多格式 | 同时维护与分享 | 内容以同一份已核对战报为准 |

用户已经在提示中写明格式时，Skill 不会重复询问。格式偏好会写入 Campaign Profile，后续回合默认沿用；用户可以随时为某一回临时指定不同格式。

### 原始转写放在哪里

原始转写属于某个 Campaign 的资料，不属于 Skill 本身。**不要把转写文件放进 `~/.codex/skills/dnd-replay`**；该目录只存放 Skill 程序文件，后续更新或重新安装时可能被替换。

长模组建议在跑团工作区中为每个 Campaign 单独建档，并把未经整理的原始资料放进 `sources/`：

```text
dnd-campaigns/<campaign-slug>/
├── campaign-profile.md
├── campaign-ledger.md
├── exports/
│   ├── session-001.docx
│   ├── session-001.pdf
│   └── session-001.txt
├── sources/
│   ├── session-001/
│   │   ├── transcript.txt
│   │   ├── combat-log.txt
│   │   └── player-notes.md
│   └── session-002/
│       └── transcript.txt
└── sessions/
    ├── session-001.md
    └── session-002.md
```

例如工作区是 `~/Documents/TRPG`，第一回原始转写可以放在：

```text
~/Documents/TRPG/dnd-campaigns/<campaign-slug>/sources/session-001/transcript.txt
```

`sources/` 保存原始资料，原则上只读、不改写；`sessions/` 保存 Skill 生成的战报。原始文件已经放在其他工作区目录时，也可以直接上传或告诉 Codex 路径，不必为了使用 Skill 强制移动。一次性整理单回时，直接在对话中上传 TXT 也可以。

### 推荐命名

```text
campaign-profile.md
sources/session-001/transcript.txt
sources/session-001/combat-log.txt
sources/session-001/player-notes.md
sources/session-002/transcript.txt
```

文件名不是硬性要求，但清楚的回合号和资料类型能减少混淆。

## 第一次使用

上传资料后，可以直接发送：

```text
$dnd-replay

这是这个 Campaign 的第一次整理，请先建立 Campaign Profile，再整理第一回战报并建立长期 Ledger。

模组名称：湮灭之墓
模组类型：长模组
当前进度：第 1 回
战报格式：Markdown + PDF，并保留 Markdown 作为长期主档
玩家角色：
- 甘道夫｜剑咏法师 | 2级
- 加坦杰厄｜幽影术士 / 厨师 | 2级
- 奎萨辛娜｜暮光牧师 | 2级
- 莱纳斯｜游荡者 / 游侠 | 2级
- 隆特｜战斗大师战士 | 2级
- 罗琳｜复仇圣武士 | 2级

模组简介：
“他不是一个英雄。他只是在一个不够善良的世界里，选择做一个善良的人。”
你们站在博德之门墓园的坡地上。
棺木里躺着慧学·邓布利多——一位本地的学者。他不曾参与战争，却庇护过无数无家可归的孤儿；他不曾被人歌颂，却让许多人在动荡的岁月里感到过安稳。
他死于死亡诅咒。
他曾在战场中为了救一个孩子被亡灵撕碎，被牧师复活。那一次他回来了。而这一次，他没有。
你们因为各自的缘分来到这里——受过他的帮助、与他同行过、或只是喝过他的一碗热汤。

转写情况：整份文件只有一个说话人标签，请根据上下文保守判断；无法确定的身份请标记，不要猜。

附件：session-01-transcript.txt
```

如果资料已经包含这些信息，Skill 会直接使用，不会重复询问。关键信息不足时，它会先提出简短问题，再开始正式战报。

## 整理后续回合

把新转写放进下一回对应的 `sources/session-XXX/`，并与现有 Campaign 档案保持在同一工作区，然后发送：

```text
$dnd-replay 整理 sources/session-002/transcript.txt。先读取现有 Campaign Profile 和 Campaign Ledger，检查与第一回的连续性，生成第二回战报并更新 Ledger。
```

默认档案结构为：

```text
dnd-campaigns/<campaign-slug>/
├── campaign-profile.md
├── campaign-ledger.md
├── exports/
│   ├── session-001.pdf
│   └── session-002.pdf
├── sources/
│   ├── session-001/
│   │   └── transcript.txt
│   └── session-002/
│       └── transcript.txt
└── sessions/
    ├── session-001.md
    └── session-002.md
```

也可以在提示中指定其他保存位置。

## 说话人不清楚时怎么写

自动推断：

```text
$dnd-replay 整理这份转写。说话人标签不可靠，请根据上下文保守推断；低置信度内容标记为身份不明。
```

提供映射：

```text
$dnd-replay 整理这份转写。说话人对应关系如下：
- 说话人 1 → DM
- 说话人 2 → 玩家小王 / 角色艾琳
- 说话人 3 → 玩家小李 / 角色洛克
```

## 查询 Campaign 历史

只要 Campaign Profile、Ledger 和各回战报仍在工作区中，就可以继续询问：

```text
$dnd-replay 第一回是谁拿到了那枚戒指？请注明来源回合。
```

```text
$dnd-replay 汇总目前所有魔法物品、当前持有者和获得来源。
```

```text
$dnd-replay 阿瑟瑞克相关的已确认线索、玩家推测和未解谜团分别有哪些？
```

## 每回输出内容

默认生成完整的读者向冒险编年史，而不是会议摘要。若只需要短版，可以在提示中明确要求“简洁战报”。完整战报固定包含：

1. 剧情经过
2. 各角色做了什么——严格按 Campaign Profile 中的实际 PC 数量逐一整理
3. 战斗记录
4. 获得的装备 / 金钱
5. NPC 关系变化
6. 已知线索
7. 未解谜团
8. 本回名场面

最后还会附上“本回结束时的队伍状态”。长模组会同时更新 Campaign Ledger。

## 事实标签

- `已确认`：转写、日志或用户说明明确支持。
- `玩家推测`：玩家提出，但尚未被剧情证实。
- `无法确定`：身份、数字、名称、结果或归属存在歧义。
- `模组背景`：用于理解世界，不代表玩家已经知道或经历。
