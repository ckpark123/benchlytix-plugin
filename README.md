# BenchLytix plugin

Dated, sourced answers from BenchLytix's published data, inside Claude Code: self-hosted replacements for paid SaaS
tools with list-price examples, what AI support vendors charge per resolution, and public facts about GitHub-hosted
MCP servers. No account and no API key.

Codex: only loading the BenchLytix server from this plugin is verified; the skills are untested in Codex.

Every answer comes from the BenchLytix MCP server at `https://www.benchlytix.com/api/mcp`, which returns each fact
with its source and the date it was read. Server documentation: https://www.benchlytix.com/docs/mcp

## Skills

- `replace-saas-tool`: what you could self-host instead of a paid tool, with each option's evidence label,
  licence, last default-branch commit and known gaps, and the paid tool's list price for your headcount, labelled
  "Example:". First prompt: "We pay for Zapier, 25 people. What could we self-host instead?"
- `compare-ai-support-pricing`: what five AI support vendors charge per resolution and how each defines a
  resolution, in their own words, side by side, from Finding 001. First prompt: "How do Intercom and Zendesk
  define a resolution, and what do they charge for one?"
- `check-mcp-repo`: the public facts about a GitHub repository before you add it as an MCP server: licence, last
  commits, contributors, commit concentration, README maintenance sentences, and BenchLytix's assessment if it
  lists the repository. First prompt: "Check n8n-io/n8n before I add it."

Each skill tells the assistant to keep every fact's date and source, print the links the server returned, and end
with the source and its date. The skills are written to give facts, not advice: they tell the assistant not to pick
an option, sum costs, or judge security. Assistants can still slip; report a wrong fact (below).

## Install (Claude Code)

```
/plugin marketplace add ckpark123/benchlytix-plugin
/plugin install benchlytix@benchlytix
```

From a shell: `claude plugin marketplace add ckpark123/benchlytix-plugin`, then
`claude plugin install benchlytix@benchlytix`.

Tools only, without the plugin:

```
claude mcp add --transport http benchlytix https://www.benchlytix.com/api/mcp
```

If you added the npm server (`benchlytix-mcp-server`) before, remove it first. If the BenchLytix server is also added
another way (by hand, or as a custom connector in your client), every tool appears twice: keep one.

Other clients (claude.ai, Cowork, Codex, ChatGPT): see https://www.benchlytix.com/docs/mcp

## Requirements

The server's schema 1.3.0 or later (every answer carries `schema_version`): 1.3.0 is the first with the plan limit note
beside each list price (`paid_tool_prices[].limit_note`), on top of the claims cap and `tested_run`, which the skills
rely on.

## What is logged

The server sends one analytics event per connect and one per tool call, never your request text or tool arguments.
The full list of fields:
https://www.benchlytix.com/privacy#hosted-mcp

## Limits

Anonymous use has rate limits; an over-limit answer says when to retry. Current limits:
https://www.benchlytix.com/docs/mcp

## Development

This repository is generated from the BenchLytix source repository (see `CONTRIBUTING.md` and `SOURCE_COMMIT`).

- Load it locally: `claude --plugin-dir .`
- Validate: `claude plugin validate --strict .` with Claude Code 2.1.281 or later (older versions reject the directory
  fields). It checks only that each MCP `url` is an absolute URL; the source repository's tests check the exact URLs.
- Evals: `claude plugin eval . --trust-plugin --no-publish --tag negative --ablation none` runs the negative cases
  on the mock tier (answers come from `evals/mocks`; no server is started). The source repository runs every tier
  against a local server built from a clean export.
- Never point evals at production.

## Reporting a wrong fact

Open a "Wrong fact" issue with the page or tool, the fact, the source URL and the date you read it.

## Licence

MIT
