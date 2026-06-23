# Awesome Ryu [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of awesome things built with and around [Ryu](https://github.com/amajorai/ryu) —
> the open-core orchestration and control layer for AI agents.

[Ryu](https://ryuhq.com) is the whole car built around AI agent engines: it sits *above* every
model and harness as the orchestration (Core) and governance (Gateway) layer. **BYO everything,
zero lock-in.** This list collects the official components, clients, SDKs, agents, tools, and
community projects in the Ryu ecosystem.

## Contents

- [Official](#official)
- [Clients & Extensions](#clients--extensions)
- [SDKs & Libraries](#sdks--libraries)
- [Agents](#agents)
- [Tools & MCP Servers](#tools--mcp-servers)
- [Engines](#engines)
- [Skills](#skills)
- [Learning & Docs](#learning--docs)
- [Community](#community)

## Official

- [Ryu](https://github.com/amajorai/ryu) — the open-core monorepo: orchestration engine (Core),
  LLM gateway (Gateway), CLI, desktop-automation and capture sidecars, and the developer SDK.
- [Documentation](https://ryuhq.com/help) — guides, the Gateway/Core reference, and interactive
  OpenAPI playgrounds.
- [Open-core boundary](https://github.com/amajorai/ryu/blob/main/docs/open-core.md) — what's open,
  what's closed, and why.

## Clients & Extensions

- [Ryu for Raycast](https://github.com/amajorai/ryu-raycast) — Ask Ryu (one-shot), Chat with Ryu
  (multi-turn), and Search Conversations, straight from Raycast (macOS + Windows). `MIT`
- [Ryu CLI](https://github.com/amajorai/ryu/tree/main/apps/cli) — a ratatui terminal client for
  Core: chat, sidecar management, sessions, and LAN node discovery. `Apache-2.0`

## SDKs & Libraries

- [@ryu/sdk](https://github.com/amajorai/ryu/tree/main/packages/sdk) — Ryu's Runnable-native dev
  SDK: `defineAgent` / `defineWorkflow` / `defineTool` / `defineSkill`, a gateway-mandatory model
  client, and MCP server/client. `Apache-2.0`
- [create-ryu-app](https://github.com/amajorai/ryu/tree/main/packages/create-ryu-app) — scaffold a
  new Ryu app/plugin: `bunx create-ryu-app <name>`. `Apache-2.0`
- [@ryu/client](https://github.com/amajorai/ryu/tree/main/packages/client) — a typed TypeScript
  client for the Core HTTP API. `Apache-2.0`

## Agents

Engines Ryu orchestrates over the [Agent Client Protocol](https://agentclientprotocol.com) (ACP) —
each is a swappable slot, none is hardcoded:

- **Ryu** (the flagship) — Pi with the Gateway on top, installed by default.
- [Pi](https://pi.dev), [Claude Code](https://www.anthropic.com), Codex, Gemini CLI, OpenClaw,
  Hermes — and ~18 more ACP agents available opt-in from the catalog.

## Tools & MCP Servers

- [Ghost](https://github.com/amajorai/ryu/tree/main/apps/ghost) — desktop-automation MCP server
  (screen perception + input control). Dual-use, consent-gated. `Apache-2.0`
- [Shadow](https://github.com/amajorai/ryu/tree/main/apps/shadow) — screen/audio/input capture,
  OCR, and semantic search. Dual-use, consent-gated. `Apache-2.0`

## Engines

Local and remote inference runtimes Ryu can drive (all swappable defaults):

- [llama.cpp](https://github.com/ggml-org/llama.cpp) (default, with Gemma 4),
  [Ollama](https://ollama.com), [vLLM](https://github.com/vllm-project/vllm),
  [SGLang](https://github.com/sgl-project/sglang), and MLX on Apple Silicon.

## Skills

- [Agent Skills](https://ryuhq.com/help) — Ryu speaks the Agent Skills standard and can browse +
  install skills from [skills.sh](https://skills.sh) (shared with Claude Code via `~/.claude/skills`).

## Learning & Docs

- [Self-hosting Ryu](https://github.com/amajorai/ryu#quick-start-self-host) — build Core + Gateway
  and point any OpenAI-compatible client at the Gateway.

## Community

- [Discord](https://ryuhq.com/discord)
- [X / Twitter](https://twitter.com/ryuhq)

## Contributing

Contributions welcome! Built something with Ryu — an agent, skill, MCP server, integration, or
guide? Open a pull request adding it to the relevant section. Please keep entries to one line, in
alphabetical order within a section, and link to a real, working resource.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/80x15.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, A Major Pte. Ltd. has waived all copyright and related or
neighboring rights to this curated list.
