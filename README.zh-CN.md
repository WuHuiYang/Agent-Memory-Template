# Agent Memory Template

[English](README.md) · [中文](README.zh-CN.md)

把这段模板交给 agent，它会为你的项目建一个**私有**记忆仓库。笔记是 git 里的 Markdown。下一次会话先 pull，读一份短索引，再就地改一条事实。

格式是 Cognition 发布的开放标准 [Agent Memory Repo](https://cognition.com/agent-memory-repo)，规范和 skill 在 [AgentMemoryRepo/agentmemoryrepo](https://github.com/AgentMemoryRepo/agentmemoryrepo)。本仓库不重新定义格式。它补上规范故意留白的用法：把共享进度写成会被就地更新的当前事实、swarm 目录、可以按计划运行的 Dreaming，以及 Cursor、Claude Code、Devin 和其他助手的操作步骤。

这个公共仓库是启动模板，不是你的记忆。不要把个人笔记、项目密钥或真实会话事实提交到这里。

## 标准里已经有的，和这个模板补上的

Cognition 的标准已经规定了兼容 agent 都要用的部分：

- 会话开始时只加载 [`MEMORY.md`](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/SPEC.md)，并且保持简短。
- 每条记忆是一行 bullet，元数据可选，形如 `[source: …; added: YYYY-MM-DD]`。键是开放的。
- 从记忆仓库根目录用 `[[path]]` 互链。Markdown 省略 `.md`。
- 会话循环是：clone 或 pull，grep 或顺着链接读，就地更新，每次编辑后 commit 并 push。
- 多个记忆仓库可以并排放。一条事实写进拥有它的那个仓库。
- [Dreaming](https://devin.ai/blog/memory-and-dreaming) 是定期整理：补上没写下来的模式，并清理记忆。
- [官方 skill](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/skills/agent-memory-repo/SKILL.md) 负责格式。它不会替你安排 Dreaming，你没要求时也不会加远程仓库。

Devin 个人 Memory Drive 的产品说明见 [Memory and Dreaming](https://docs.devin.ai/product-guides/memory)。那份个人记忆不存会话摘要、PR 编号这类任务状态、密钥，以及很容易重新查到的事实。本模板不放宽这些限制。

| 标准里已经有 | 本模板补上 |
| --- | --- |
| 格式和官方 skill | [SPEC-NOTES.md](SPEC-NOTES.md)：指向规范，并列出我们的约定 |
| 写教训的地方 | [conventions.md](conventions.md)：省 token，以及一条事实该放哪个文件 |
| 会话循环 | [AGENTS.md](AGENTS.md)：Cursor、Claude Code、Devin 和其他助手 |
| Dreaming 这个角色 | [DREAMING.md](DREAMING.md)：一次整理要做什么，以及可定时粘贴的提示 |
| 官方文里的 swarm 目录 | [swarms/README.md](swarms/README.md)，外加一个很小的虚构例子 |
| 团队记忆 | [progress/README.md](progress/README.md)：当前状态，就地改，不写日记 |

如果要改格式，请到官方仓库提议。这里的约定和规范不一致时，以规范为准。

## 目录

```text
MEMORY.md                  入口；会话先只加载这个文件
AGENTS.md                  每个 agent 怎么读、怎么写
conventions.md             token、归属、安全
DREAMING.md                定期整理，以及那次任务的提示
SPEC-NOTES.md              规范和约定的边界
tooling.md                 工具主题的起始文件
projects/                  能留下来的笔记；example-payments.md 是虚构的
progress/                  当前状态，就地更新；其中的样例是虚构的
swarms/                    一次并行调查一个目录；样例是虚构的
prompts/setup.md           中英文启动提示
skills/agent-memory-template/SKILL.md
```

文件名以 `example-` 开头，或标题里写着 `EXAMPLE` 的，都是用来看形状的虚构内容。建真实仓库时删掉。它们不是记忆。

## 建一个记忆仓库

把下面的提示贴进一次新的 agent 会话，补上尖括号里的内容。英文全文在 [README.md](README.md) 和 [prompts/setup.md](prompts/setup.md)。

短提示：

```text
照着 https://github.com/WuHuiYang/Agent-Memory-Template 这个启动模板，帮我为 <项目名> 设置一套完整的记忆系统。请创建一个独立的私有记忆仓库（不要写进业务项目里），按模板结构初始化，并根据我补充的项目信息填好 MEMORY.md 索引和第一批主题文件。
```

完整提示：

```text
照着 https://github.com/WuHuiYang/Agent-Memory-Template 这个启动模板，帮我为 <项目名> 设置一套完整的记忆系统。格式以 Cognition 的 Agent Memory Repo 为准（https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/SPEC.md）。不要另起一套格式，也不要把这个公共模板当成规范本身。

- 创建一个独立的私有记忆仓库。不要把记忆写进业务项目仓库，不要提交到 https://github.com/WuHuiYang/Agent-Memory-Template ，也不要提交到 https://github.com/AgentMemoryRepo/agentmemoryrepo 。
- 第一次 push 之前先跟我确认：目标仓库是私有的，并且我有写权限。如果你是从公共模板 clone 的，在写入任何真实事实之前，把 remote 改成我的私有仓库。
- 按模板初始化：MEMORY.md、AGENTS.md、conventions.md、DREAMING.md、tooling.md、SPEC-NOTES.md、projects/、progress/、swarms/、skills/agent-memory-template/。标成 EXAMPLE 的文件在写好真实笔记后删掉；不需要样本的话现在就删。在私有仓库里，把本模板的 README.md 和 README.zh-CN.md 换成一份短说明：写上项目名，并指向 AGENTS.md。公共 README 描述的是启动模板，不是我的记忆。
- 采访我，或使用我下面贴出的项目信息，写一份短的 MEMORY.md（只放每次会话都需要的事实，加上 [[路径]] 索引）和第一批主题文件。一条事实一行。有来源时加上 [source: …; added: YYYY-MM-DD]。不要存密钥、会话摘要或 PR 状态。
- 能反复用到的教训放进 projects/ 或 tooling.md。如果有正在进行的协作，progress/ 里只保留当前状态、阻塞和下一步，之后就地改这几行，不要追加日记。
- 为当前这个 agent 安装或改写 skill。官方格式：npx skills add AgentMemoryRepo/agentmemoryrepo --skill agent-memory-repo 。本模板（进度、swarm、Dreaming、私有远程）：npx skills add WuHuiYang/Agent-Memory-Template --skill agent-memory-template 。如果用 Devin，安装官方插件 `devin plugins install AgentMemoryRepo/agentmemoryrepo`，不要把本模板整个仓库当成插件安装。
- 完成后告诉我本地完整路径和私有远程 URL，并用四步说明以后的会话：git pull --ff-only、只加载 MEMORY.md、grep 或顺着 [[链接]] 读、就地更新并在每次编辑后 commit/push。不要 force-push，不要 git add -A。
- 可选：按 DREAMING.md 里的提示，帮我安排定期 Dreaming。不要对着这个公共模板仓库安排。

项目信息（可选；空着就问我）：
<贴上你已经知道的偏好、项目名和踩坑>
```

做完之后你应该拿到：

- 一个私有仓库，`origin` 是你的，不是这个模板。
- 一份根据你提供的事实写成的短 `MEMORY.md`。
- 项目的主题文件，EXAMPLE 样例已经去掉。
- 装在你所用 agent 上的 skill。
- 对下一次会话的简短说明；如果你要求了，还有 Dreaming 的安排。

## 下一次会话

同一台机器、磁盘还在，用本地路径就够。云端 agent 或另一台电脑需要那个私有远程。

```text
使用 agent-memory-template 这个 skill，私有记忆仓库在 <路径或 URL>。先 git pull --ff-only。只加载 MEMORY.md，再 grep 或顺着链接读。<这次的任务>
```

事实变了就改原来的那一行，然后 commit、push。不要把这次会话追加成一篇日志。

## Skill

```bash
npx skills add AgentMemoryRepo/agentmemoryrepo --skill agent-memory-repo
npx skills add WuHuiYang/Agent-Memory-Template --skill agent-memory-template
```

Devin 自己有个人 Memory Drive，也有内置 Dreaming。你自己的仓库，安装官方格式插件，并把会话指到那个私有仓库：

```bash
devin plugins install AgentMemoryRepo/agentmemoryrepo
```

不要把本模板仓库当成 Devin 插件安装。仓库根上的 `AGENTS.md` 会被注进每一次会话。请只安装 `skills/agent-memory-template`。

其他能用 git 的助手，包括 Grok 风格的 bot，走同一套循环。把私有仓库 URL 写进助手的设置。笔记放在 git 里，不要只放在助手的隐藏提示里。

## 当作 GitHub 模板使用

在 GitHub 上点 **Use this template**，新建仓库时选 **Private**。这样只是把启动文件复制到你拥有的仓库，不会把你的笔记写回这个公共仓库。如果没有这个按钮，仓库所有者可以在 Settings → General 里打开 Template repository。也可以不点按钮，直接粘贴上面的启动提示，让 agent 复制这套目录。

无论哪种方式，真实记忆只提交到私有仓库。推回 `WuHuiYang/Agent-Memory-Template` 等于公开。

适合这个仓库的 topics：`agent-memory`、`ai-agents`、`llm`、`cursor`、`claude`。

## 许可

本模板以 [MIT](LICENSE) 授权，版权归 WuHuiYang。Agent Memory Repo 的格式和官方 skill 在[它们自己的仓库](https://github.com/AgentMemoryRepo/agentmemoryrepo)里也是 MIT，版权归其作者。本项目不重新许可那份规范。
