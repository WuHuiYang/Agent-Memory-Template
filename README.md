# Agent Memory Template

[English](README.md) · [中文](README.zh-CN.md)

A starter you can hand to an agent to create a **private** memory repo for your project. The notes are Markdown in git. The next session pulls them, reads a short index, and updates a fact in place.

The format is [Agent Memory Repo](https://cognition.com/agent-memory-repo), the open standard Cognition published, with the spec and skill in [AgentMemoryRepo/agentmemoryrepo](https://github.com/AgentMemoryRepo/agentmemoryrepo). This repository does not redefine that format. It fills in the operating habits the spec leaves open: shared progress as current truth, swarm folders, a Dreaming job you can schedule, and procedures for Cursor, Claude Code, Devin, and other assistants.

This public repository is the starter. It is not your memory. Do not commit personal notes, project secrets, or real session facts here.

## The standard, and what this adds

Cognition's standard already covers the pieces every compatible agent needs:

- [`MEMORY.md`](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/SPEC.md) is the only file loaded at session start, and it stays short.
- Each entry is one bullet, with optional `[source: …; added: YYYY-MM-DD]` metadata. Keys are open.
- `[[path]]` links from the memory root. Omit `.md` for Markdown.
- The session loop is clone or pull, grep or follow links, update in place, commit and push after every edit.
- Several memory repos can sit side by side. Write each fact to the repo that owns it.
- [Dreaming](https://devin.ai/blog/memory-and-dreaming) is a periodic pass that adds missing patterns and cleans memory.
- The [official skill](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/skills/agent-memory-repo/SKILL.md) installs the format. It does not schedule Dreaming, and it does not pick a remote unless you ask.

Product detail for Devin's personal drive: [Memory and Dreaming](https://docs.devin.ai/product-guides/memory). That drive does not store session summaries, task state such as pull-request numbers, secrets, or facts that are cheap to rediscover. This template does not relax that.

| You get this from the standard | This template adds |
| --- | --- |
| The format and the official skill | [SPEC-NOTES.md](SPEC-NOTES.md), which points at the spec and lists our conventions |
| A place to write lessons | [conventions.md](conventions.md) for token use and which file owns a fact |
| The session loop | [AGENTS.md](AGENTS.md) for Cursor, Claude Code, Devin, and other assistants |
| Dreaming as a role | [DREAMING.md](DREAMING.md), a job and a prompt you can run on a schedule |
| Swarm folders in the official walkthrough | [swarms/README.md](swarms/README.md) plus a small fictional example |
| Team memory | [progress/README.md](progress/README.md): current status, edited in place, never a diary |

Format changes belong in the official repository. If a convention here ever disagrees with the spec, follow the spec.

## Layout

```text
MEMORY.md                  entry point; a session loads this file first
AGENTS.md                  how every agent reads and writes memory
conventions.md             token budget, ownership, safety
DREAMING.md                periodic cleanup, and the prompt that runs it
SPEC-NOTES.md              spec vs convention
tooling.md                 starter topic file
projects/                  durable notes; example-payments.md is fictional
progress/                  current status, edited in place; the sample is fictional
swarms/                    one folder per parallel investigation; the sample is fictional
prompts/setup.md           the setup prompt in English and Chinese
skills/agent-memory-template/SKILL.md
```

Files whose names start with `example-`, and headings that say `EXAMPLE`, are fiction so you can see the shape. Delete them when you create a real repo. They are not memory.

## Set up a memory repo

Copy this into a fresh agent session. Fill the angle brackets. The same text is in [prompts/setup.md](prompts/setup.md), with a Chinese version.

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

Short Chinese prompt (full text in [README.zh-CN.md](README.zh-CN.md)):

```text
照着 https://github.com/WuHuiYang/Agent-Memory-Template 这个启动模板，帮我为 <项目名> 设置一套完整的记忆系统。请创建一个独立的私有记忆仓库（不要写进业务项目里），按模板结构初始化，并根据我补充的项目信息填好 MEMORY.md 索引和第一批主题文件。
```

What you should have afterwards:

- A private repository whose `origin` is yours, not this template.
- A short `MEMORY.md` written from facts you supplied.
- Topic files for the project, with EXAMPLE samples gone.
- The skill installed for the agent you used.
- A one-paragraph explanation of the next session, and a Dreaming schedule if you asked for one.

## The next session

On one machine with a persistent disk, the local path is enough. A cloud agent or a new computer needs the private remote.

```text
Use the agent-memory-template skill with the private memory repo at <path or URL>. Pull --ff-only. Load only MEMORY.md, then grep or follow links. <task>
```

The agent updates a bullet when a fact changes, commits, and pushes. It does not append a log of the session.

## Skills

```bash
npx skills add AgentMemoryRepo/agentmemoryrepo --skill agent-memory-repo
npx skills add WuHuiYang/Agent-Memory-Template --skill agent-memory-template
```

Devin already has a personal Memory Drive and built-in Dreaming. For a repo you own, install the official format plugin and point the session at that private repo:

```bash
devin plugins install AgentMemoryRepo/agentmemoryrepo
```

Do not install this template repository as a Devin plugin. Its root `AGENTS.md` would be injected into every session. Copy or install `skills/agent-memory-template` instead.

Any other assistant that can use git, including a Grok-style bot, uses the same loop. Put the private repo URL in the assistant's setup. Keep the notes in git, not only in the assistant's hidden prompt.

## Use this repository as a template

On GitHub, use **Use this template** and create the new repository as **Private**. That copies these starter files into a repository you own. If the button is missing, enable Template repository under Settings → General. You can also skip the button and paste the setup prompt; the agent copies the layout for you.

Either way, real memory is committed only to the private repo. Pushing notes back to `WuHuiYang/Agent-Memory-Template` publishes them.

Topics that fit this repository: `agent-memory`, `ai-agents`, `llm`, `cursor`, `claude`.

## License

This template is [MIT](LICENSE), copyright WuHuiYang. The Agent Memory Repo format and the official skill are MIT in [their repository](https://github.com/AgentMemoryRepo/agentmemoryrepo), copyright their authors. This project does not relicense that spec.
