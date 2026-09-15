# Codex entry point

The canonical Crux instructions remain in the adjacent `CLAUDE.md` file and in
`~/.claude/CLAUDE.md`. Read the adjacent file before doing substantive work,
read the global file when it exists, and follow both as project instructions.
When working below this directory, also read the closest nested `CLAUDE.md`
before changing that project.

Translate surface-specific mechanics as follows:

- Invoke a named workflow as `$skill-name` in Codex when the Claude instructions
  show `/skill-name`.
- Use Codex's current model and planning controls; references to choosing Opus or
  Sonnet describe the Claude Code workflow rather than a project requirement.
- Map Claude tool names and permission syntax to the equivalent Codex tools and
  approval model. Preserve the stated intent, safety boundary, and stopping
  condition.
- Use a writable temporary directory or the current workspace when a skill names
  Claude-only paths such as `/home/claude` or `/mnt/user-data`.

Keep the Claude setup intact. Add Codex-specific compatibility under `AGENTS.md`,
`.agents/`, `.codex/`, or `.codex-plugin/` unless the user explicitly asks to
change the shared source.
