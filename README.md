# Awesome Ryu

[![Awesome](https://shieldcn.dev/badge/Awesome-Ryu-73DC8C.svg?logo=awesomelists&logoColor=white)](https://github.com/amajorai/ryu) [![Discord](https://shieldcn.dev/discord/1439211418724597800.svg?logo=discord&logoColor=white&color=4B78E6)](https://ryuhq.com/discord) [![X](https://shieldcn.dev/badge/Follow-@ryuhq-FA9BFA.svg?logo=x&logoColor=white)](https://twitter.com/ryuhq)

> A curated list of awesome things built with and around [Ryu](https://github.com/amajorai/ryu), the open platform for agent orchestration and human collaboration.

Ryu is the open platform for agent orchestration and human collaboration — the whole stack around AI agent engines. It sits *above* every model and harness as the orchestration (Core) and governance (Gateway) layer: tools, security, memory, cost saving, and routing, all built in. **BYO everything, zero lock-in.** This list collects the official components, clients, SDKs, agents, tools, apps, and community projects in the Ryu ecosystem.

## Contents

- [Official](#official)
- [Clients & Surfaces](#clients--surfaces)
- [SDKs & Libraries](#sdks--libraries)
- [Feature Apps](#feature-apps)
- [Plugins & MCP Servers](#plugins--mcp-servers)
- [Marketplace Plugins](#marketplace-plugins)
- [Agents](#agents)
- [Engines](#engines)
- [Skills](#skills)
- [Learning & Docs](#learning--docs)
- [Community](#community)
- [Catalog status legend](#catalog-status-legend)

## Catalog status legend

The app and plugin tables use the same lifecycle vocabulary:

- **Built-in** — compiled into the Ryu/Core distribution and available before the marketplace is reachable.
- **System** — a Core-owned/protected runtime package; System is separate from Built-in and does not by itself mean the package is compiled into Core.
- **Pre-installed** — Core creates an enabled lifecycle record for it on a fresh install. It can still be disabled, and it is separate from Built-in and System.
- **Stability** — the manifest `stability` field (stable, beta, alpha, rc, or another declared value). An omitted field means stable; this is a maturity label, not an update channel.
- **Hidden** — the listing is hidden from the normal catalog view; it does not change whether the package is built-in, system, or pre-installed.

## Official

| Repo | What it is |
| --- | --- |
| [Ryu](https://github.com/amajorai/ryu) | The open platform for agent orchestration and human collaboration. The open-core monorepo — the orchestration engine (Core), the LLM control layer (Gateway: routing, firewall, cache, evals, audit), terminal clients, the SDK, and Ghost/Shadow. |
| [Documentation](https://docs.ryuhq.com) | Guides, the Gateway/Core reference, and interactive OpenAPI playgrounds. |
| [Docs repo](https://github.com/amajorai/ryu-docs) | The source for the site above, generated from `apps/fumadocs`. |
| [Open-core boundary](https://github.com/amajorai/ryu/blob/main/docs/open-core.md) | What's open, what's closed, and why. |

## Clients & Surfaces

| Client | What it is |
| --- | --- |
| [Ryu TUI](https://github.com/amajorai/ryu/tree/main/apps/tui) | The recommended terminal client (Bun/OpenTUI) — chat, sidecar management, sessions, node discovery. |
| [Ryu CLI](https://github.com/amajorai/ryu/tree/main/apps/cli) | The legacy terminal client for Core (Rust/ratatui), **superseded by `apps/tui`**; retains headless script-shaped subcommands. `Apache-2.0` |
| [Ryu for Raycast](https://github.com/amajorai/ryu-raycast) | Ask Ryu (one-shot), Chat with Ryu (multi-turn), and Search Conversations, straight from Raycast (macOS + Windows). `MIT` |
| [ryu-mcp](https://github.com/amajorai/ryu/tree/main/apps/mcp) | An MCP server that exposes a running Ryu Core node to any MCP host (Claude Desktop, Cursor, …) — agents, models, skills, and registered MCP servers behind one bridge. |
| [Ryu Desktop](https://github.com/amajorai/ryu/tree/main/apps/desktop) | The flagship app (Tauri v2 + React). Source-available in the hub mirror; grab the installers from [ryuhq.com/download](https://ryuhq.com/download). |
| [Ryu Web](https://ryuhq.com) | Hosted marketing, dashboard, and billing surface for the managed tier. |

## SDKs & Libraries

| Package | What it is |
| --- | --- |
| [@ryuhq/sdk](https://github.com/amajorai/ryu/tree/main/packages/sdk) | Ryu's Runnable-native dev SDK, with `defineAgent` / `defineWorkflow` / `defineTool` / `defineSkill`, a gateway-mandatory model client, and MCP server/client. `Apache-2.0` |
| [create-ryu-app](https://github.com/amajorai/ryu/tree/main/packages/create-ryu-app) | Scaffold a new Ryu app/plugin with `bunx create-ryu-app <name>`. `Apache-2.0` |
| [@ryuhq/client](https://github.com/amajorai/ryu/tree/main/packages/client) | A typed TypeScript client for the Core HTTP API. `Apache-2.0` |
| [@ryuhq/core-client](https://github.com/amajorai/ryu/tree/main/packages/core-client) | The platform-agnostic typed Core client used by the TUI, native, and MCP surfaces. |
| [@ryuhq/protocol](https://github.com/amajorai/ryu/tree/main/packages/protocol) | Surface-agnostic wire-format contracts shared across clients. |

## Feature Apps

Manifest-driven feature apps ship as their own satellite repos (`amajorai/ryu-<app>`), each with real release assets, grouped by their manifest category:

### Automation

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/predict-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/predict-light.png" width="32" alt="ryu-predict" /></picture> | [Autocomplete](https://github.com/amajorai/ryu-predict) | – | – | – | experimental | – | 0.1.14 | Inline ghost-text autocomplete in any text field on your machine, accepted with Tab. A… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/recipes-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/recipes-light.png" width="32" alt="ryu-recipes" /></picture> | [Recipes](https://github.com/amajorai/ryu-recipes) | – | – | – | experimental | – | 0.1.14 | Desktop-automation recipes: record → save → replay UI action sequences. Backed by… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/warmup-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/warmup-light.png" width="32" alt="ryu-warmup" /></picture> | [Warmup](https://github.com/amajorai/ryu-warmup) | – | – | – | experimental | – | 0.1.14 | Starts your subscription agents' rolling usage windows on your own schedule: a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/webhooks-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/webhooks-light.png" width="32" alt="ryu-webhooks" /></picture> | [Webhooks](https://github.com/amajorai/ryu-webhooks) | – | – | ✓ | experimental | – | 0.1.14 | Inbound webhook endpoint registry: resolved public URLs, secret presence,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/workflows-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/workflows-light.png" width="32" alt="ryu-workflows" /></picture> | [Workflows](https://github.com/amajorai/ryu-workflows) | – | – | – | experimental | – | 0.1.14 | Workflows: petgraph DAG automation with triggers, durable execution, and a… |

### Browsers

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/browser-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/browser-light.png" width="32" alt="ryu-browser" /></picture> | [Browser](https://github.com/amajorai/ryu-browser) | ✓ | ✓ | – | stable | – | 0.1.14 | A real-Chromium browser (Electron) Ryu runs as a local sidecar and exposes as the… |

### Communication

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mail-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mail-light.png" width="32" alt="ryu-mail" /></picture> | [Mail](https://github.com/amajorai/ryu-mail) | – | – | – | experimental | – | 0.1.14 | Agent Inboxes — email as a service for agents. Runs the out-of-process ryu-mail… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/meetings-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/meetings-light.png" width="32" alt="ryu-meetings" /></picture> | [Meetings](https://github.com/amajorai/ryu-meetings) | – | – | – | experimental | – | 0.1.14 | Meeting notes: record → live transcript → AI notes, auto-saved into the Meetings Space… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/teams-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/teams-light.png" width="32" alt="ryu-teams" /></picture> | [Teams](https://github.com/amajorai/ryu-teams) | – | – | – | experimental | – | 0.1.14 | Teams: named groups of agents you can address as one. Governance shell over the… |

### Creative

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/canvas-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/canvas-light.png" width="32" alt="ryu-canvas" /></picture> | [Canvas](https://github.com/amajorai/ryu-canvas) | – | – | – | experimental | – | 0.1.14 | A node board for generative media: wire up image, video, chat, text-to-speech,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/whiteboard-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/whiteboard-light.png" width="32" alt="ryu-whiteboard" /></picture> | [Whiteboard](https://github.com/amajorai/ryu-whiteboard) | – | – | – | experimental | – | 0.1.14 | An Excalidraw whiteboard shipped as a Ryu app: draw, diagram, and rearrange freely,… |

### Developer Tools

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/blueprint-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/blueprint-light.png" width="32" alt="ryu-blueprint" /></picture> | [Blueprint](https://github.com/amajorai/ryu-blueprint) | – | – | – | experimental | – | 0.1.14 | Review an agent's plan before it touches a file. The agent publishes its plan over… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/finetune-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/finetune-light.png" width="32" alt="ryu-finetune" /></picture> | [Fine-tuning](https://github.com/amajorai/ryu-finetune) | – | – | – | experimental | – | 0.1.14 | A LoRA/QLoRA training studio: launch fine-tune jobs on this node's GPU or a remote Ryu… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/healing-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/healing-light.png" width="32" alt="ryu-healing" /></picture> | [Self-Healing](https://github.com/amajorai/ryu-healing) | – | – | – | experimental | – | 0.1.14 | Self-healing: failed runs are diagnosed by a Gateway side-model and proposed fixes are… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/monitors-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/monitors-light.png" width="32" alt="ryu-monitors" /></picture> | [Monitors](https://github.com/amajorai/ryu-monitors) | – | – | – | experimental | – | 0.1.14 | Website monitors: price, stock, keyword, content, and uptime watches with cross-device… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/simulator-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/simulator-light.png" width="32" alt="ryu-simulator" /></picture> | [Simulators](https://github.com/amajorai/ryu-simulator) | – | – | – | experimental | – | 0.1.14 | Drive iOS Simulators (macOS + Xcode) and Android Emulators from a workspace tab. Ryu… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/skill-editor-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/skill-editor-light.png" width="32" alt="ryu-skill-editor" /></picture> | [Skill Editor](https://github.com/amajorai/ryu-skill-editor) | – | – | – | experimental | – | 0.1.14 | Author a user-owned Agent Skill (SKILL.md): front-matter fields (name / description /… |

### Documents

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/docling-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/docling-light.png" width="32" alt="ryu-docling" /></picture> | [Docling](https://github.com/amajorai/ryu-docling) | – | – | – | experimental | – | 0.1.14 | Document parsing via IBM's MIT-licensed Docling — the highest-fidelity… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/markitdown-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/markitdown-light.png" width="32" alt="ryu-markitdown" /></picture> | [MarkItDown](https://github.com/amajorai/ryu-markitdown) | – | – | ✓ | experimental | – | 0.1.14 | Document parsing via Microsoft's MIT-licensed MarkItDown library — the default… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mineru-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mineru-light.png" width="32" alt="ryu-mineru" /></picture> | [MinerU](https://github.com/amajorai/ryu-mineru) | – | – | – | experimental | – | 0.1.14 | Document parsing via MinerU (opendatalab) — the highest-fidelity `document.parse`… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/unstructured-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/unstructured-light.png" width="32" alt="ryu-unstructured" /></picture> | [Unstructured](https://github.com/amajorai/ryu-unstructured) | – | – | – | experimental | – | 0.1.14 | Document parsing via the Apache-2.0 Unstructured library — the broadest-coverage… |

### Knowledge & Memory

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/learning-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/learning-light.png" width="32" alt="ryu-learning" /></picture> | [Learning](https://github.com/amajorai/ryu-learning) | – | – | ✓ | experimental | – | 0.1.14 | Learning loop: turn chats and runs into reusable skills, gated by the approval Inbox,… |

### Media & Voice

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/clips-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/clips-light.png" width="32" alt="ryu-clips" /></picture> | [Clips](https://github.com/amajorai/ryu-clips) | – | – | – | experimental | – | 0.1.14 | Clips: capture and browse screen/timeline clips. A Core→Shadow proxy that depends on… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/subtitles-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/subtitles-light.png" width="32" alt="ryu-subtitles" /></picture> | [Subtitles](https://github.com/amajorai/ryu-subtitles) | – | – | – | experimental | – | 0.1.14 | Pick a video on this machine, transcribe it locally, translate the transcript into the… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/voice-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/voice-light.png" width="32" alt="ryu-voice" /></picture> | [Voice](https://github.com/amajorai/ryu-voice) | – | – | ✓ | experimental | – | 0.1.14 | Voice data path: speech-to-text transcription (whisper.cpp) and text-to-speech… |

### Productivity

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/activity-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/activity-light.png" width="32" alt="ryu-activity" /></picture> | [Activity](https://github.com/amajorai/ryu-activity) | – | – | – | experimental | – | 0.1.14 | The unified activity feed: everything happening on this node — monitor alerts,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/calendar-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/calendar-light.png" width="32" alt="ryu-calendar" /></picture> | [Calendar](https://github.com/amajorai/ryu-calendar) | – | – | ✓ | experimental | – | 0.1.14 | The scheduled-runs calendar: every agent and workflow scheduled job projected onto… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/crm-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/crm-light.png" width="32" alt="ryu-crm" /></picture> | [Harbor](https://github.com/amajorai/ryu-crm) | – | – | – | experimental | – | 0.1.14 | A CRM that starts as a data model rather than a fixed set of screens. Harbor ships the… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/dashboards-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/dashboards-light.png" width="32" alt="ryu-dashboards" /></picture> | [Dashboards](https://github.com/amajorai/ryu-dashboards) | – | – | – | experimental | – | 0.1.14 | Dashboards: composable widget boards that assemble live views over monitors, meetings,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/drafts-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/drafts-light.png" width="32" alt="ryu-drafts" /></picture> | [Drafts](https://github.com/amajorai/ryu-drafts) | – | – | – | experimental | – | 0.1.14 | A durable outbox for messages you have not sent yet. Anything you type into a composer… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mission-control-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/mission-control-light.png" width="32" alt="ryu-mission-control" /></picture> | [Mission Control](https://github.com/amajorai/ryu-mission-control) | – | – | – | experimental | – | 0.1.14 | The project-level view over many chats: recent sessions and what each one… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/news-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/news-light.png" width="32" alt="ryu-news" /></picture> | [Wire](https://github.com/amajorai/ryu-news) | – | – | – | experimental | – | 0.1.14 | Your own newsroom, running on your node. Wire pulls RSS, Atom and JSON Feed in on a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/quests-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/quests-light.png" width="32" alt="ryu-quests" /></picture> | [Quests](https://github.com/amajorai/ryu-quests) | – | – | – | experimental | – | 0.1.14 | Quests: auto-detecting todos surfaced from your chats and activity, tracked as a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/rlm-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/rlm-light.png" width="32" alt="ryu-rlm" /></picture> | [Recursive Language Model](https://github.com/amajorai/ryu-rlm) | – | – | – | experimental | – | 0.1.14 | Answer questions about a corpus far larger than any model's context window — without… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/social-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/social-light.png" width="32" alt="ryu-social" /></picture> | [Outpost](https://github.com/amajorai/ryu-social) | – | – | – | experimental | – | 0.1.14 | A publishing command center for every social account you run: compose once, tailor per… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/timeline-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/timeline-light.png" width="32" alt="ryu-timeline" /></picture> | [Timeline](https://github.com/amajorai/ryu-timeline) | – | – | – | experimental | – | 0.1.14 | The activity replay timeline: a CapCut-style scrubber over Shadow's captured… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/tuition-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/tuition-light.png" width="32" alt="ryu-tuition" /></picture> | [Tuition](https://github.com/amajorai/ryu-tuition) | – | – | – | experimental | – | 0.1.14 | A tutor for one learner — you. Point it at your own syllabus, chapter or notes and it… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/ugc-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/ugc-light.png" width="32" alt="ryu-ugc" /></picture> | [UGC](https://github.com/amajorai/ryu-ugc) | – | – | – | experimental | – | 0.1.14 | Creator-marketing campaign tracker: briefs, a creator roster, post submissions with… |

### Research

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/research-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/research-light.png" width="32" alt="ryu-research" /></picture> | [Research](https://github.com/amajorai/ryu-research) | – | – | – | experimental | – | 0.1.14 | Deep research: multi-step web research runs backed by the autoresearch sidecar, with… |

### Security

| | App | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/approvals-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/approvals-light.png" width="32" alt="ryu-approvals" /></picture> | [Approvals](https://github.com/amajorai/ryu-approvals) | – | – | – | experimental | – | 0.1.14 | Approval inbox: a human-in-the-loop queue where agent-proposed actions, edits, and… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/reasoning-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/app-icons/reasoning-light.png" width="32" alt="ryu-reasoning" /></picture> | [Automated Reasoning](https://github.com/amajorai/ryu-reasoning) | – | – | – | experimental | – | 0.1.14 | Check an answer against a written policy with a solver instead of a second opinion.… |

Icons are the same tiles the satellite and marketplace READMEs render from each app's `manifest.json`, served from [ryu-marketplace](https://github.com/amajorai/ryu-marketplace) `app-icons/` in light and dark.

## Plugins & MCP Servers

| Repo | What it is |
| --- | --- |
| [Ryu Marketplace](https://github.com/amajorai/ryu-marketplace) | The grouped plugin registry — **41 first-party plugins** (40 official `@ryu/*`), each a self-contained manifest, installed with `ryu add <plugin>`. |
| [Ghost](https://github.com/amajorai/ghost) | Desktop-automation MCP server (screen perception + input control). Dual-use, consent-gated. `Apache-2.0` |
| [Shadow](https://github.com/amajorai/shadow) | Screen/audio/input capture, OCR, and semantic search. Dual-use, consent-gated. `Apache-2.0` |

## Marketplace Plugins

All first-party plugins from the marketplace above, grouped by their manifest category:

### Automation

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/agent-comms/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/agent-comms/icon-light.png" width="28" alt="" /></picture> | [Switchboard](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/agent-comms/) | – | – | – | experimental | – | 0.1.14 | Lets the agents on this node talk to each other. Any agent can look up who else is… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/bytebot/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/bytebot/icon-light.png" width="28" alt="" /></picture> | [Bytebot Desktop](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/bytebot/) | – | – | – | experimental | – | 0.1.14 | Drives a Bytebot desktop (https://github.com/bytebot-ai/bytebot) through `bytebotd`,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/ghost/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/ghost/icon-light.png" width="28" alt="" /></picture> | [Ghost](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/ghost/) | ✓ | ✓ | ✓ | stable | – | 0.1.14 | Desktop automation: 29 screen perception and input control tools. Cross-platform… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-subagent/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-subagent/icon-light.png" width="28" alt="" /></picture> | [Subagents](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/pi-subagent/) | – | – | ✓ | experimental | – | 0.1.14 | Adds the Task tool to the managed Pi agent, so it can delegate a bounded,… |

### Browsers

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/agentbrowser/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/agentbrowser/icon-light.png" width="28" alt="" /></picture> | [Agent Browser](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/agentbrowser/) | ✓ | ✓ | ✓ | stable | – | 0.1.14 | Browser automation via the `agent-browser` CLI's MCP server… |

### Developer Tools

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/headroom/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/headroom/icon-light.png" width="28" alt="" /></picture> | [Headroom Compression](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/headroom/) | – | – | – | experimental | – | 0.1.14 | Context compression (chopratejas/headroom): compress tool outputs, logs, files, and… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/hook-observers/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/hook-observers/icon-light.png" width="28" alt="" /></picture> | [Hook Observers](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/hook-observers/) | – | – | – | experimental | – | 0.1.14 | A worked reference for the turn-hook events Ryu can fire: five observer hooks watching… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/hook-session-context/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/hook-session-context/icon-light.png" width="28" alt="" /></picture> | [Session Context](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/hook-session-context/) | – | – | – | experimental | – | 0.1.14 | Injects the current date and time at the start of every session, so the agent stops… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-monitor/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-monitor/icon-light.png" width="28" alt="" /></picture> | [Monitor](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/pi-monitor/) | – | – | ✓ | experimental | – | 0.1.14 | Adds the monitor tool to the managed Pi agent, so it can watch a command or WebSocket… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-shell/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pi-shell/icon-light.png" width="28" alt="" /></picture> | [Background Bash](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/pi-shell/) | – | – | ✓ | experimental | – | 0.1.14 | Adds bash_background / bash_output / bash_kill to the managed Pi agent, so a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pxpipe/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/pxpipe/icon-light.png" width="28" alt="" /></picture> | [pxpipe](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/pxpipe/) | – | – | – | experimental | – | 0.1.14 | Token-saving loopback proxy (https://github.com/teamchong/pxpipe): it renders the… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/rtk/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/rtk/icon-light.png" width="28" alt="" /></picture> | [RTK (Rust Token Killer)](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/rtk/) | – | – | – | experimental | – | 0.1.14 | Run a dev command through RTK (Rust Token Killer) and get a token-compressed version… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/sample/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/sample/icon-light.png" width="28" alt="" /></picture> | [Research Assistant](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/sample/) | – | – | – | experimental | ✓ | 0.1.14 | The reference plugin: a minimal example that declares one of each runnable kind — an… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/sample-widget/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/sample-widget/icon-light.png" width="28" alt="" /></picture> | [Sample Widget](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/sample-widget/) | – | – | – | experimental | ✓ | 0.1.14 | Reference third-party MCP widget plugin. A tiny local Node MCP server (server.mjs)… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/toolsmith-example/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/toolsmith-example/icon-light.png" width="28" alt="" /></picture> | [toolsmith-example](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/toolsmith-example/) | – | – | – | experimental | ✓ | 0.1.14 | Worked example for tools/toolsmith — a real, verified inline_deno tool. Not registered… |

### Knowledge & Memory

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/honcho/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/honcho/icon-light.png" width="28" alt="" /></picture> | [Honcho](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/honcho/) | – | – | – | experimental | – | 0.1.14 | Give the swappable `memory` layer a provider that MODELS the user instead of only… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/mem0/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/mem0/icon-light.png" width="28" alt="" /></picture> | [Mem0](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/mem0/) | – | – | – | experimental | – | 0.1.14 | Read and write a hosted Mem0 memory project (https://mem0.ai) through the Mem0… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/no-more-mistakes/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/no-more-mistakes/icon-light.png" width="28" alt="" /></picture> | [No More Mistakes](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/no-more-mistakes/) | – | – | – | experimental | – | 0.1.14 | Notices when you correct the agent, writes the lesson down as a one-line rule in a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/shadow/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/shadow/icon-light.png" width="28" alt="" /></picture> | [Shadow](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/shadow/) | ✓ | ✓ | ✓ | stable | – | 0.1.14 | Search everything Shadow has captured (screen text, audio transcripts, input) and… |

### Productivity

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/chat-title/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/chat-title/icon-light.png" width="28" alt="" /></picture> | [Chat Title](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/chat-title/) | – | – | ✓ | experimental | – | 0.1.14 | Auto-renames a chat as soon as the first reply lands, then again after every N… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/goal/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/goal/icon-light.png" width="28" alt="" /></picture> | [Goal](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/goal/) | – | – | ✓ | experimental | – | 0.1.14 | Give the agent a goal with `/goal` and it keeps working until a judge model agrees the… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/no-ai-slop/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/no-ai-slop/icon-light.png" width="28" alt="" /></picture> | [No AI Slop](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/no-ai-slop/) | – | – | – | experimental | – | 0.1.14 | Bundles the `no-ai-slop` editing skill and runs it on every finished answer: a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/output-styles/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/output-styles/icon-light.png" width="28" alt="" /></picture> | [Output Styles](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/output-styles/) | – | – | ✓ | experimental | – | 0.1.15 | The ten built-in output styles — ELI5, I have ADHD, Explanatory, Learning, Proactive,… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/plan-continue/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/plan-continue/icon-light.png" width="28" alt="" /></picture> | [Plan Continue](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/plan-continue/) | – | – | – | experimental | – | 0.1.14 | While plan mode is on and the plan has not been accepted, this injects a follow-up… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/recap/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/recap/icon-light.png" width="28" alt="" /></picture> | [Recap](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/recap/) | – | – | – | experimental | – | 0.1.14 | Ends a long agent turn with a short recap of what it actually did — the work, the… |

### Research

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/advisor/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/advisor/icon-light.png" width="28" alt="" /></picture> | [Advisor](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/advisor/) | – | – | – | experimental | – | 0.1.14 | Consult a stronger reviewer model for a second opinion — as an auto-review turn hook… |

### Search

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/brave/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/brave/icon-light.png" width="28" alt="" /></picture> | [Brave Search](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/brave/) | – | – | – | experimental | – | 0.1.14 | Independent web search via the Brave Search API (https://brave.com/search/api/),… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/exa/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/exa/icon-light.png" width="28" alt="" /></picture> | [Exa Search](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/exa/) | – | – | ✓ | experimental | – | 0.1.14 | Neural and keyword web search via the Exa API (https://exa.ai), exposed as two… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/firecrawl/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/firecrawl/icon-light.png" width="28" alt="" /></picture> | [Firecrawl](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/firecrawl/) | – | – | – | experimental | – | 0.1.14 | Web search and page scraping via the Firecrawl v2 API (https://firecrawl.dev), exposed… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/parallel/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/parallel/icon-light.png" width="28" alt="" /></picture> | [Parallel Search](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/parallel/) | – | – | – | experimental | – | 0.1.14 | Web search and content extraction via Parallel (https://parallel.ai), exposed as three… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/scrapling/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/scrapling/icon-light.png" width="28" alt="" /></picture> | [Scrapling](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/scrapling/) | – | – | – | experimental | – | 0.1.14 | Adaptive web-page extraction via the Scrapling MCP server… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/serper/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/serper/icon-light.png" width="28" alt="" /></picture> | [Serper](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/serper/) | – | – | – | experimental | – | 0.1.14 | Google's own search results as JSON via the Serper API (https://serper.dev), plus… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/spider/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/spider/icon-light.png" width="28" alt="" /></picture> | [Spider](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/spider/) | – | – | ✓ | experimental | – | 0.1.14 | High-performance web crawling and content extraction via the Spider CLI… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/spidercloud/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/spidercloud/icon-light.png" width="28" alt="" /></picture> | [Spider Cloud](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/spidercloud/) | – | – | – | experimental | – | 0.1.14 | Hosted multi-page web crawling via the Spider Cloud API (https://spider.cloud),… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/tavily/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/tavily/icon-light.png" width="28" alt="" /></picture> | [Tavily Search](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/tavily/) | – | – | – | experimental | – | 0.1.14 | Search-and-extract for agents via the Tavily API (https://tavily.com), exposed as two… |

### Security

| | Plugin | Built-in | System | Pre-installed | Stability | Hidden | Version | What it is |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/double-check/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/double-check/icon-light.png" width="28" alt="" /></picture> | [Double Check](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/double-check/) | – | – | ✓ | experimental | – | 0.1.14 | Sends every answer to a second model for review before you act on it, so mistakes get… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/firewall/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/firewall/icon-light.png" width="28" alt="" /></picture> | [Gateway Firewall](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/firewall/) | – | – | – | experimental | – | 0.1.14 | An on/off switch over the Gateway's built-in firewall, which screens model traffic for… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/proof/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/proof/icon-light.png" width="28" alt="" /></picture> | [Proof of Work](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/proof/) | – | – | ✓ | experimental | – | 0.1.14 | The stricter sibling of `/goal`: an independent verifier agent has to prove with… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/receipts/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/receipts/icon-light.png" width="28" alt="" /></picture> | [Receipts](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/receipts/) | – | – | ✓ | experimental | – | 0.1.14 | Verify work with visual evidence: `/receipt <goal>` makes the agent capture a… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/security-guidance/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/security-guidance/icon-light.png" width="28" alt="" /></picture> | [Security Guidance](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/security-guidance/) | – | – | – | experimental | – | 0.1.14 | Scans each answer for security vulnerabilities and has a second model review the code… |
| <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/tool-firewall/icon-dark.png" /><img src="https://raw.githubusercontent.com/amajorai/ryu-marketplace/main/plugins/tool-firewall/icon-light.png" width="28" alt="" /></picture> | [Tool Firewall](https://github.com/amajorai/ryu-marketplace/tree/main/plugins/tool-firewall/) | – | – | – | experimental | – | 0.1.14 | A worked reference for pre- and post-tool hooks: the pre hook denies any tool call… |

## Agents

Engines Ryu orchestrates over the [Agent Client Protocol](https://agentclientprotocol.com) (ACP). Each is a swappable slot, none is hardcoded:

| Agent | Notes |
| --- | --- |
| **Ryu** (the flagship) | Pi with the Gateway on top, installed by default. |
| [Pi](https://pi.dev), [Claude Code](https://www.anthropic.com), Codex, Gemini CLI, OpenClaw, Hermes | Plus ~18 more ACP agents available opt-in from the catalog. |

## Engines

Local and remote inference runtimes Ryu can drive (all swappable defaults):

| Engine | Role |
| --- | --- |
| [llama.cpp](https://github.com/ggml-org/llama.cpp) | The default local engine (with Gemma 4). |
| [Ollama](https://ollama.com), [vLLM](https://github.com/vllm-project/vllm), [SGLang](https://github.com/sgl-project/sglang), MLX | Swappable local/remote runtimes. |

## Skills

| Skill | What it is |
| --- | --- |
| [Agent Skills](https://docs.ryuhq.com/docs/extend/skills) | Ryu speaks the Agent Skills standard and can browse + install skills from [skills.sh](https://skills.sh) (shared with Claude Code via `~/.claude/skills`). |
| Official skills | Taught to agents so they can drive Ryu itself: [setup-ryu](https://github.com/amajorai/ryu/tree/main/apps/skills/setup-ryu), [ryu-author-skill](https://github.com/amajorai/ryu/tree/main/apps/skills/ryu-author-skill), [ryu-build-agent](https://github.com/amajorai/ryu/tree/main/apps/skills/ryu-build-agent), [ryu-local-model](https://github.com/amajorai/ryu/tree/main/apps/skills/ryu-local-model), [ryu-mcp](https://github.com/amajorai/ryu/tree/main/apps/skills/ryu-mcp). |

## Learning & Docs

| Resource | What it is |
| --- | --- |
| [Self-hosting Ryu](https://github.com/amajorai/ryu#quick-start-self-host) | Build Core + Gateway and point any OpenAI-compatible client at the Gateway. |
| [One-click deploy](https://github.com/amajorai/ryu#one-click-deploy) | Render, Railway, DigitalOcean, Docker Compose, and Fly.io. |
| [OpenAPI playgrounds](https://docs.ryuhq.com/docs/extend/develop/api-reference) | Interactive Core and Gateway API reference. |

## Community

| Where | What it is |
| --- | --- |
| [Discord](https://ryuhq.com/discord) | The Ryu community server. |
| [X / Twitter](https://twitter.com/ryuhq) | Announcements and updates. |

## Contributing

Contributions welcome! Built something with Ryu — an agent, skill, MCP server, integration, app, or guide? Open a pull request adding it to the relevant section. Keep entries to one line and link to a real, working resource.

This list is generated from the Ryu monorepo and synchronized to this public repository. Additions
and corrections are welcome: open a pull request here and follow
[CONTRIBUTING.md](./CONTRIBUTING.md). A sync may rewrite generated content. Icons are not stored
here - they render from [ryu-marketplace](https://github.com/amajorai/ryu-marketplace)
`app-icons/` / `plugins/<name>/`.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/80x15.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, A Major Pte. Ltd. has waived all copyright and related or neighboring rights to this curated list.
