# Swarms

A swarm is a folder where agents working in parallel share one investigation. The pattern is part of the official [Agent Memory Repo](https://cognition.com/agent-memory-repo) writeup (the slow-checkout example in that article and in the [official README](https://github.com/AgentMemoryRepo/agentmemoryrepo)). This page is how to open a folder. It is not a second copy of that story.

Create one folder per investigation:

```text
swarms/<slug>/
  README.md        goal and rules
  findings.md      what agents have measured, including ruled-out causes
  questions.md     questions across areas, with answers nested under them
  agents/
    <area>.md      one notes file per agent
```

Add a `scripts/` file only when every agent must run the same command. Link it with the extension: `[[swarms/<slug>/scripts/bench.sh]]`.

## Rules

- The swarm `README.md` states the goal, how to measure, and which files to write. Keep it short enough to reread before each step.
- Before each step, pull and read `findings.md` and `questions.md`.
- Write measurements in `findings.md`, including what you ruled out. Update a bullet when the measurement changes.
- If another area might explain what you see, ask in `questions.md`. The agent who knows answers under that question.
- All agents write the shared files. When a push is rejected, read both versions and write one bullet. Do not force-push.
- Per-agent files are for notes that do not belong in the shared board. The conclusion still goes in `findings.md`.
- When the swarm ends, add one index link if a later session should reuse the folder. Copy any durable lesson into the project note. Dreaming may remove the folder later only after that lesson has a home and the folder is unused. The default is to keep it.

[example-flaky-search/](example-flaky-search/README.md) is a small fictional folder so the layout is visible. It is not the official example, and it is not a real incident. Delete it in a real repo.
