---
title: Roles & Access
weight: 3
---

SK Wwise MCP supports **role-based access control** by enabling different combinations of servers per user. This lets teams give AI capabilities that match each person's responsibilities — junior sound designers get read-only access, while build engineers get full pipeline control.

## Recommended Roles

| Role | Servers | What They Can Do |
|------|---------|------------------|
| **Sound Designer (Junior)** | Browse, Audition, Media Read | Explore the project, preview sounds, inspect audio sources |
| **Sound Designer (Senior)** | + Objects, Containers | Create and edit objects, configure containers and routing |
| **Build Engineer** | + Pipeline, Command Line | Import audio, generate SoundBanks, run CLI operations |
| **QA / Profiling** | + Profiling, Profiling Control, Remote | Profile performance, connect to devkits, capture sessions |
| **Admin** | All servers | Full access to every tool |

## How to Configure

When running `setup.bat` or `setup.sh`, you'll be prompted to select which servers to enable. The script generates a `.mcp.json` file with only the selected servers.

To change the configuration later, edit `.mcp.json` directly — add or remove server entries as needed.

## Why Split Into Servers?

Two reasons:

1. **Safety** — Fewer tools means fewer ways for an AI agent to make unintended changes. A junior designer's agent literally cannot delete objects if the Objects server isn't enabled.

2. **Accuracy** — LLMs select tools more reliably from smaller sets. 12 focused servers with ~8 tools each outperform a single server with 95 tools.
