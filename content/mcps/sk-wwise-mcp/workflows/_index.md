---
title: Common Workflows
weight: 4
---

Step-by-step guides for typical tasks. You don't need to know which tools are called — just describe what you want in plain language and the AI agent handles the rest.

## Find and Fix

Locate an issue in your project and apply a fix.

**Servers needed:** Browse, Objects

1. Ask the agent to find the problem — e.g., *"Find all sounds with volume above 0 dB"*
2. Review the results
3. Ask for the fix — e.g., *"Set all of those to 0 dB"*
4. Verify — *"Confirm the volumes are now 0 dB"*

## Import and Configure Audio

Bring audio files into Wwise and set up the full signal chain.

**Servers needed:** Pipeline, Objects, Containers

1. **Import** — *"Import all .wav files from C:/audio/footsteps/ into a new Random Container called Footsteps"*
2. **Configure containers** — *"Set up random playback with no repeats"*
3. **Create Events** — *"Create a Play event for the Footsteps container"*
4. **Add to SoundBank** — *"Add the Footsteps event to the Main SoundBank and generate"*

## Profile a Game Session

Connect to a running game and analyze performance.

**Servers needed:** Remote, Profiling Control, Profiling

1. **Connect** — *"Show available remote consoles"* then *"Connect to the PS5 devkit"*
2. **Start capture** — *"Start a profiler capture"*
3. **Analyze** — *"What are the top 10 voices by CPU?"* or *"Show bus levels"*
4. **Stop and save** — *"Stop the capture and save the results"*
5. **Disconnect** — *"Disconnect from the remote console"*

## Bulk Operations

Make changes across many objects at once.

**Servers needed:** Browse, Objects

- *"Find all sounds under Weapons/ that have 3D Spatialization disabled and enable it"*
- *"Rename all objects matching 'SFX_' to replace the prefix with 'sfx_'"*
- *"Set the output bus to 'SFX_Bus' for every Sound under the Foley hierarchy"*

## Create a New Project

Start a new Wwise project from scratch (no WAAPI needed).

**Servers needed:** Command Line

- *"Create a new Wwise project at C:/MyGame/MyGame.wproj targeting Windows and PS5"*

## Wwise 2025.1+ Note

Wwise 2025.1 renamed the top-level hierarchies:

| Pre-2025.1 | 2025.1+ |
|-------------|---------|
| `\Actor-Mixer Hierarchy` | `\Containers` |
| `\Master-Mixer Hierarchy` | `\Busses` |

All tools use **2025.1+ names** by default. If you're on an older version of Wwise, adjust paths accordingly.
