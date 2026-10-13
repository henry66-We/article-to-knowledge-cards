# Make Knowledge Cards

将 Markdown 或纯文本材料整理为便于复习的知识卡片。Skill 位于 [`skills/make-knowledge-cards`](skills/make-knowledge-cards)，入口文件是 [`SKILL.md`](skills/make-knowledge-cards/SKILL.md)。

## 1. 项目解决什么问题

长篇笔记和文章不方便快速复习。本项目帮助读者从原文中提取重点、合并重复信息，并整理成简短、可回忆和自测的卡片，同时避免加入原文没有支持的结论。

## 2. 主要功能

- 支持 Markdown（`.md`、`.markdown`）和纯文本（`.txt`）文件。
- 每份材料通常生成 5–8 张卡片；材料内容不足时不靠重复或编造凑数。
- 每张卡片包含标题、核心知识、简明解释，以及例子或附答案的自测题。
- 默认保留原文语言；多份文件分别整理，保留来源区分。
- 可将结果保存为与源文件对应的 `.cards.md` 文件。

## 3. 安装方法

将 `skills/make-knowledge-cards` 整个文件夹复制到 Codex 的个人 Skills 目录：如果设置了 `CODEX_HOME`，放到 `$CODEX_HOME/skills/`；否则放到 `~/.codex/skills/`。目录结构应为：

```text
skills/
└── make-knowledge-cards/
    ├── SKILL.md
    └── agents/
        └── openai.yaml
```

Windows PowerShell 示例（在项目根目录运行；若设置了 `CODEX_HOME`，请将目标路径改为该目录下的 `skills`）：

```powershell
$target = Join-Path $env:USERPROFILE '.codex\skills'
New-Item -ItemType Directory -Force $target | Out-Null
Copy-Item -Recurse '.\skills\make-knowledge-cards' $target
```

安装后在 Codex 中开始新对话并调用 `$make-knowledge-cards`。

## 4. 使用方法

提供 `.md`、`.markdown` 或 `.txt` 文件，并说明要整理成知识卡片。例如：

> 使用 `$make-knowledge-cards`，把这份笔记整理成便于复习的知识卡片，并保存为 Markdown 文件。

也可以直接粘贴文章内容，并要求按知识卡片格式整理。

## 5. 输入与输出示例

**输入示例**（`photosynthesis.txt`）：

```text
植物利用阳光，将水和二氧化碳转化为糖，并释放氧气。叶绿素吸收蓝光和红光，反射绿光。
```

**输出示例**：

### 卡片 1：光合作用的基本过程

- **核心知识**：植物利用阳光，将水和二氧化碳转化为糖，并释放氧气。
- **简明解释**：光合作用把光能转化为储存在糖中的化学能。
- **例子或自测题**：光合作用释放什么气体？**答案：氧气。**
