# 开口 kaikou

一个教口头表达的 Agent skill。生活小事、面试、汇报,任何要开口的场景都能练;没想法也能一句话开始。你先讲,老师用你自己的话反问你;新手可以拿一张结构卡,但你必须自己讲出来才算,老师不替你讲,不给稿。带记忆,每次知道你上次练到哪。

当前版本 0.3.1。版本计划见 `版本规划.md`。

## 装法

**Claude Code / Codex 等读 skills 目录的 Agent**

在你想存练习记录的文件夹里执行(PowerShell;Git Bash 的 `ln -s` 对目录会复制而不是链接,不要用):

```
git clone https://github.com/xgz123-wq/kaikou .agents/skills/kaikou
New-Item -ItemType SymbolicLink -Path "$HOME\.agents\skills\kaikou" -Target "$PWD\.agents\skills\kaikou"
New-Item -ItemType SymbolicLink -Path "$HOME\.claude\skills\kaikou" -Target "$HOME\.agents\skills\kaikou"
```

New-Item 报「需要管理员权限」时,改用 `cmd /c mklink /J <链接路径> <目标路径>` 建目录联接,效果相同,不需要权限。

老师和你的练习记录在同一个文件夹,用户目录只放链接。然后在这个文件夹里打开 Agent,说「我今天要讲一件事」。学生档案会自动建在那个文件夹的 `学生档案/` 下,是你的私人数据,不要跟老师一起上传。

**只有项目目录的 Agent**

根目录建 `AGENTS.md` 写一行:

```
先读 .agents/skills/kaikou/SKILL.md,按它工作。
```

**没有文件系统的 Agent(豆包、网页聊天)**

把 `SKILL.md`、`references/点评清单.md`、`references/记忆规范.md`、`references/题源.md`、`references/结构卡.md`、`references/场景-生活小事.md` 六个文件的内容整段贴给它,或者直接给它本仓库的链接让它读。然后每次开场把你本地 `学生档案/短期记忆.md` 的内容贴给它,练完它会把该存的内容整理给你,你自己存回文件。

## 目录

按 Agent Skill 官方结构分层:`SKILL.md` 是入口,每次都读;`references/` 按需读;`assets/` 放模板。

```
kaikou/
├── SKILL.md                 引擎:老师底线、入口、教法档位、练习循环、记忆
├── references/              用到才读
│   ├── 记忆规范.md          学生档案五个文件加素材目录怎么写、什么时候升级
│   ├── 点评清单.md          核心 6 项打分标准,所有场景通用
│   ├── 结构卡.md            K1～K7 按题型的结构卡,一次只给一张
│   ├── 题源.md              生活小事场景的四类通用题,每题标默认卡
│   └── 场景-生活小事.md     默认场景;一个场景一个文件,都用「场景-」开头
├── assets/
│   └── 场景模板.md          加一个场景 = 复制它,填好存成 references/场景-XX.md
├── README.md                本文件,给人看
├── 版本规划.md              已做、在做、下一步
└── LICENSE
```
