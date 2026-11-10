# Setup prompts

Copy one prompt into a fresh agent session. Fill the angle brackets. Leave a blank the agent can ask about rather than inventing a fact.

The agent must create a **separate private** memory repo. It must not write memory into the application repo, into [AgentMemoryRepo/agentmemoryrepo](https://github.com/AgentMemoryRepo/agentmemoryrepo), or into this public template.

The same prompts are shown in [README.md](../README.md) and [README.zh-CN.md](../README.zh-CN.md).

## English

```text
Follow https://github.com/WuHuiYang/Agent-Memory-Template as a starter layout. The format is Cognition's Agent Memory Repo (https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/SPEC.md). Do not invent a new format, and do not treat this template as the spec.

Set up a complete memory system for <project name>.

- Create a SEPARATE private git repository for memory. Never write memory into the application or business repo. Never commit memory to https://github.com/WuHuiYang/Agent-Memory-Template or to https://github.com/AgentMemoryRepo/agentmemoryrepo.
- Confirm with me that the destination is private and that I own it (or I am allowed to write) before the first push. If you clone this template, change the remote to my private repo before you write any real fact.
- Initialize the template structure: MEMORY.md, AGENTS.md, conventions.md, DREAMING.md, tooling.md, SPEC-NOTES.md, projects/, progress/, swarms/, and skills/agent-memory-template/. Delete files marked EXAMPLE once real notes replace them, or sooner if I do not need the samples. In the private repo, replace this template's README.md and README.zh-CN.md with a short note that names the project and points at AGENTS.md. Those public READMEs describe the starter, not my memory.
- Interview me, or use the project facts I paste below, to fill a short MEMORY.md (only what every session needs, plus an index of [[path]] links) and the first topic files. One fact per line. Use [source: …; added: YYYY-MM-DD] when you have a source. Do not store secrets, session summaries, or pull-request status.
- Put durable lessons in projects/ or tooling.md. If there is shared work in flight, put only the current status, blocker, and next step in progress/, and edit those lines in place later. Do not start a diary.
- Install or adapt the skill for this agent. Official format skill: npx skills add AgentMemoryRepo/agentmemoryrepo --skill agent-memory-repo. This template's skill (progress, swarms, Dreaming, private remote): npx skills add WuHuiYang/Agent-Memory-Template --skill agent-memory-template. On Devin, install the official plugin with `devin plugins install AgentMemoryRepo/agentmemoryrepo`, and do not install this whole template repo as a plugin.
- After setup, tell me the full path and the private remote URL. Explain later sessions in four steps: pull --ff-only, load only MEMORY.md, grep or follow [[path]] links, update in place and commit/push after every edit. No force-push. No git add -A.
- Optionally help me schedule Dreaming with the prompt in DREAMING.md. Do not schedule it against this public template.

Project facts (optional; ask me if this is empty):
<paste preferences, project names, and gotchas you already know>
```

## 中文

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
