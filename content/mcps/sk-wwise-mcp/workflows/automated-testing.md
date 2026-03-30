---
title: Automated Testing
weight: 6
---

SK Wwise MCP has three layers of testing — **unit**, **integration**, and **eval** — all built on Python and [pytest](https://docs.pytest.org/).

## Unit Tests

**~450 tests** across 27 files in `tests/unit/`. All WAAPI calls are mocked, so no Wwise installation is required.

**Coverage includes:**

- Core modules — WAAPI dispatcher, query engine, audio conversion, CLI wrapper
- Business logic — pipeline operations, transport, profiling, object manipulation
- MCP servers — one test file per server (browse, objects, containers, pipeline, etc.)

```bash
uv run pytest tests/unit/ -v
```

## Integration Tests

**8 test files** in `tests/integration/`, marked with `@pytest.mark.integration`. These run against a **live Wwise headless server** with a test project.

**What they test:**

- Object queries, creation, deletion, and modification
- Switch/Blend Container assignments
- Audio import and SoundBank operations
- Transport/playback operations
- Audio peaks and Media Pool reads
- Generic WAAPI passthrough

The `conftest.py` fixtures handle setup automatically:

1. Locate WwiseConsole via `WWISEROOT` or the Windows registry
2. Start a headless WAAPI server on port 8080
3. Wait up to 20 seconds for the connection
4. Clean up leftover test objects before and after each run

```bash
uv run pytest tests/integration/ -v
```

To skip integration tests when running the full suite:

```bash
uv run pytest tests/ -v -m "not integration"
```

## Eval Tests (LLM Routing)

**39 test cases** in `tests/eval/` that verify the AI agent selects the correct MCP tools for a given prompt. This catches routing regressions when tools or server configurations change.

Each case defines a prompt and the expected tool(s):

```json
{
  "id": 1,
  "prompt": "Ping Wwise to check if it's available",
  "expected_tools": ["ping_wwise"],
  "category": "browse"
}
```

**Categories:** browse, audition, generic, objects, media-read, cross-server.

### Running Evals

Eval runs use Claude Code skills for orchestration:

1. **Setup** — create a test project and start the WAAPI server:

   ```text
   /eval-setup
   ```

2. **Run cases** — choose batch (5 cases/invocation) or granular (1 case):

   ```text
   /loop 60s /eval-batch
   /loop 30s /eval-routing
   ```

3. **Generate report:**

   ```bash
   python tests/eval/report.py
   ```

4. **Cleanup:**

   ```text
   /eval-teardown
   ```

A `PostToolUse` hook in `.claude/settings.json` automatically logs every Wwise MCP tool call to `tests/eval/tool_log.jsonl` during eval runs. The `verify.py` script compares actual vs. expected tools and writes results to `test_results.json`.

## Artifacts

| File | Purpose |
| ---- | ------- |
| `tests/eval/tool_log.jsonl` | Timestamped MCP tool calls |
| `tests/eval/test_results.json` | Pass/fail results per case |
| `tests/eval/setup_manifest.json` | Eval project path, WAAPI PID, created objects |

## Prerequisites

| Test layer | Requirements |
| ----------- | ------------ |
| Unit | Python 3.12+, `pytest>=8.0` |
| Integration | + Wwise installed, `WWISEROOT` set or discoverable via registry |
| Eval | + Claude Code with SK Wwise MCP servers configured |

Install dev dependencies:

```bash
uv sync   # installs runtime + dev deps, creates .venv
```
