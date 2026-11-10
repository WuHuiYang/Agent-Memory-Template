# Progress

A progress file is the current truth for one shared effort. Agents read it to see the status. They edit it when the status changes.

Use this folder when several agents share work in flight. That is the team-memory use case in the [official standard](https://cognition.com/agent-memory-repo). The `progress/` name and the in-place rules below are conventions of this template. Devin's personal Memory Drive does not store task state, and this folder is not a place to record pull-request numbers over time.

## Rules

- One file per effort, named for the subject: `progress/<slug>.md`.
- A few bullets, usually status, blocker, and next step. That is the whole file.
- When a bullet becomes wrong, rewrite it or delete it in the same commit. Do not add a new dated line under it.
- Do not record session summaries, pull-request numbers, CI statuses, or a timeline of what each agent did.
- When the work finishes, move any durable lesson into `projects/` or another topic file. Then delete the progress bullets, or leave a single line if a later session must know that nothing is in flight: `- No active work [updated: YYYY-MM-DD]`.
- Link the progress file from the project note. Keep it out of `MEMORY.md` unless every session truly needs that status.

[example-payments.md](example-payments.md) shows the shape. It is fiction. Replace it.
