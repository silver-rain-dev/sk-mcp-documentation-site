---
title: Servers & Tools
weight: 2
---

SK Wwise MCP is split into **12 specialized servers**, each with a focused set of tools. This modular design keeps AI agents accurate — smaller tool sets mean better tool selection.

## Server Overview

| Server | Tools | Purpose |
|--------|------:|---------|
| **Browse** | 14 | Read-only queries, object inspection, property discovery |
| **Objects** | 8 | Create, delete, rename, move, copy objects; set properties |
| **Containers** | 9 | Switch/Blend container assignments, state groups, randomizers, attenuation |
| **Pipeline** | 9 | Audio import, SoundBank management, project save |
| **Audition** | 4 | Transport-based playback preview |
| **Media Read** | 3 | Audio source analysis (peaks), Media Pool queries |
| **UI** | 13 | UI automation — layouts, commands, selection, screenshots |
| **Profiling** | 12 | Read-only profiler data (voices, CPU, busses, RTPCs) |
| **Profiling Control** | 7 | Profiler capture control, meter registration |
| **Remote** | 4 | Remote connection to devkits and game instances |
| **Command Line** | 9 | WwiseConsole CLI (works without WAAPI) |
| **Generic** | 3 | Fallback — discover and call any WAAPI function |

## Browse

Read-only server for exploring your Wwise project. Safe to enable for all users.

**14 tools** covering object queries, search, property inspection, type discovery, and object comparison.

Example prompts:
- *"Show me all Events in my Wwise project"*
- *"How many Sound objects are under Containers?"*
- *"Compare the settings between Footstep_Walk and Footstep_Run"*

## Objects

Create, modify, and manage Wwise objects.

**8 tools** for object CRUD operations and property management.

Example prompts:
- *"Create a new Random Container called 'Footsteps' under Containers"*
- *"Rename all objects matching 'temp_' to remove the prefix"*
- *"Set the volume of Ambience_Forest to -6 dB"*

## Containers

Manage container-specific configurations like switch assignments, blend tracks, and state groups.

**9 tools** for container logic and routing.

Example prompts:
- *"Assign Surface_Grass to the 'Grass' state in the Footstep switch container"*
- *"Set up a blend container with distance-based crossfade"*

## Pipeline

Handle audio file import and SoundBank generation.

**9 tools** for the asset pipeline.

{{% details title="Audio Format Support" %}}
WAAPI natively imports **WAV** files. If you have OGG, FLAC, or MP3 files, SK Wwise MCP can auto-convert them to WAV using ffmpeg (must be installed separately).
{{% /details %}}

Example prompts:
- *"Import all .wav files from C:/audio/ into a Random Container"*
- *"Generate SoundBanks for the Main bank"*
- *"Save the Wwise project"*

## Audition

Preview sounds using Wwise's transport system.

**4 tools** for playback control.

Example prompts:
- *"Play the sound at \\Containers\\Default Work Unit\\Footstep"*
- *"Stop all playing transports"*

## Media Read

Inspect audio sources and the Media Pool.

**3 tools** for audio analysis.

## UI

Automate the Wwise authoring UI.

**13 tools** for layout management, command execution, selection, and screenshots.

## Profiling

Read profiler data from a running game or preview session.

**12 tools** covering voice counts, CPU usage, bus metering, and RTPC values.

Example prompts:
- *"What's the CPU usage in the profiler right now?"*
- *"Show me the loudest busses"*

## Profiling Control

Control profiler capture sessions.

**7 tools** for starting/stopping captures, registering meters, and saving results.

## Remote

Connect to remote platforms for profiling.

**4 tools** for discovering and connecting to devkits and game instances.

## Command Line

Run WwiseConsole CLI operations. **Does not require WAAPI** — works with the Wwise command-line tool directly.

**9 tools** for headless project operations.

Example prompts:
- *"Create a new Wwise project at C:/MyGame/MyGame.wproj for Windows and PS5"*

## Generic

Fallback server for any WAAPI call not covered by the specialized servers.

**3 tools** — discover available WAAPI functions, inspect their schemas, and call them directly.
