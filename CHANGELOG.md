# Changelog

One entry per version. The version here equals `version` in `.claude-plugin/plugin.json` and
`.codex-plugin/plugin.json`. Minor for a skill or a behaviour, patch for wording.

## 1.0.1 (2026-11-23)

- README only: the evals line no longer mentions a budget ledger. No skill, eval or server change.

## 1.0.0 (2026-11-23)

- The plugin skeleton: the Claude and Codex manifests, the marketplace file, and the BenchLytix MCP server
  (`https://www.benchlytix.com/api/mcp`, tagged `?via=claude_plugin` or `?via=codex_plugin`). Needs the server's
  schema 1.3.0 or later.
- Three skills: `replace-saas-tool` (self-hosted options and list-price examples), `compare-ai-support-pricing`
  (Finding 001) and `check-mcp-repo` (public facts about a GitHub repository), each with its output shape, the
  words it never uses and its refusal templates inside its SKILL.md, so no answer depends on the model reading
  another file.
