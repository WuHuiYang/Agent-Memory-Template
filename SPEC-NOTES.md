# Spec notes

This template follows the [Agent Memory Repo format](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/SPEC.md) as published. It does not define a second format.

The spec is the Format section of [cognition.com/agent-memory-repo](https://cognition.com/agent-memory-repo), maintained in [AgentMemoryRepo/agentmemoryrepo](https://github.com/AgentMemoryRepo/agentmemoryrepo). The official skill is [`skills/agent-memory-repo/SKILL.md`](https://github.com/AgentMemoryRepo/agentmemoryrepo/blob/main/skills/agent-memory-repo/SKILL.md). Devin's product behavior is documented in [Memory and Dreaming](https://docs.devin.ai/product-guides/memory) and the [launch post](https://devin.ai/blog/memory-and-dreaming).

## What we keep unchanged

- `MEMORY.md` is the only file a session loads up front. It stays short: facts every session needs, then an index.
- A Markdown entry is one bullet on one line. Optional metadata is `[key: value; key: value]`. Keys are open. `source` and `added` (`YYYY-MM-DD`) are the recommended keys.
- Cross-links are `[[path]]` from the memory root. Omit `.md` for Markdown. Keep other extensions, such as `.sql`.
- The session loop is clone or pull, then grep or follow links, then update in place, then commit and push after every edit.
- Several memory repos can sit side by side. Write each fact to the repo that owns it.
- Dreaming is a periodic pass that adds missing patterns and cleans memory. The official skill does not schedule that pass for you.

If a file in this template disagrees with the spec, the spec wins. Propose format changes in the [official repository](https://github.com/AgentMemoryRepo/agentmemoryrepo), not here.

## What this template adds

These are operating conventions for a repo you own. They are not part of the spec.

| Convention | Where |
| --- | --- |
| Token use, file ownership, and what not to store | [conventions.md](conventions.md) |
| Session procedure for Cursor, Claude Code, Devin, and other agents | [AGENTS.md](AGENTS.md) |
| Shared status as current truth, edited in place | [progress/README.md](progress/README.md) |
| How to run a swarm folder | [swarms/README.md](swarms/README.md) |
| A Dreaming job you can run on a schedule | [DREAMING.md](DREAMING.md) |
| A skill that applies the conventions and a private remote | [skills/agent-memory-template/SKILL.md](skills/agent-memory-template/SKILL.md) |
| One prompt that creates the private repo | [prompts/setup.md](prompts/setup.md) |

Personal memory, in Devin's Memory Drive, does not store session summaries, task state such as PR numbers and statuses, secrets, or facts that are cheap to rediscover. This template keeps that rule. Shared work follows the official team-memory and swarm use cases. In this template, `progress/` holds the current status and is edited in place, project notes hold durable lessons, and `swarms/` holds a parallel investigation in the official folder shape. `progress/` is a convention of this template, not a field in the spec. Keep all three free of session diaries.
