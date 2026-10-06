# 开口 kaikou

一个教口头表达的 Agent skill。你讲一段 1 分钟的生活小事,老师用你自己的话反问你,引导你自己搭框架再讲一遍,不替你讲,不给稿。带记忆,每次知道你上次练到哪。

当前版本 0.1.1(MVP)。版本计划见 `版本规划.md`。

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

把 `SKILL.md`、`点评清单.md`、`记忆规范.md`、`题库.md`、`开口模板.md` 五个文件的内容整段贴给它,或者直接给它本仓库的链接让它读。然后每次开场把你本地 `学生档案/短期记忆.md` 的内容贴给它,练完它会把该存的内容整理给你,你自己存回文件。

## 目录

| 文件 | 作用 |
|---|---|
| `SKILL.md` | 老师的角色、教法、流程,主文件 |
| `点评清单.md` | 6 项打分标准 |
| `题库.md` | 分 4 类的生活题 |
| `开口模板.md` | 金字塔讲法(未核对原书) |
| `记忆规范.md` | 学生档案五个文件怎么写、什么时候升级 |
| `版本规划.md` | 已做、在做、下一步 |
