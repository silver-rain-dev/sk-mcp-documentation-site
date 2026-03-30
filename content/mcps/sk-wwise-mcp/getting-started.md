---
title: Getting Started
weight: 1
---

Get SK Wwise MCP installed and connected to your Wwise project.

## Prerequisites

- **Python 3.12+**
- **Wwise 2024.1+** with WAAPI enabled
- **uv** (recommended) or pip
- An MCP-compatible AI agent (Claude Code, Cursor, VS Code Copilot, etc.)

Optional:
- **ffmpeg** — for auto-converting non-WAV audio formats during import

## Installation

### Windows

```bash
git clone https://github.com/silver-rain-dev/sk-wwise-mcp
cd sk-wwise-mcp/sk-wwise-mcp
setup.bat
```

### macOS / Linux

```bash
git clone https://github.com/silver-rain-dev/sk-wwise-mcp
cd sk-wwise-mcp/sk-wwise-mcp
./setup.sh
```

The setup script will:
1. Install dependencies via `uv` (or `pip` as fallback)
2. Let you choose which servers to enable
3. Generate a `.mcp.json` with the correct paths

### Manual Installation

If you prefer manual setup:

```bash
cd sk-wwise-mcp/sk-wwise-mcp
uv sync
# or: python -m venv .venv && .venv/Scripts/pip install -e .
```

Then add servers to your MCP configuration (`.mcp.json` for project-level, or `~/.claude.json` for global):

```json
{
  "mcpServers": {
    "sk-wwise-browse": {
      "command": "/path/to/.venv/Scripts/python.exe",
      "args": ["/path/to/mcp_browse/server.py"]
    }
  }
}
```

## Enable WAAPI in Wwise

Most servers require WAAPI to be running:

1. Open Wwise
2. Go to **Project > User Preferences**
3. Check **Enable Wwise Authoring API**
4. Restart Wwise if prompted

## Verify the Connection

Once configured, ask your AI agent:

> Ping Wwise to check if it's available.

If the connection is working, you'll get a confirmation with the Wwise version and project name.

## Next Steps

- [Explore servers and tools](../servers) to see what's available
- [Set up role-based access](../roles) for your team
- [Try common workflows](../workflows) to get productive quickly
