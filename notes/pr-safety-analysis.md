# PR Safety Controls — Analysis & Proposal

**Date:** March 2026  
**Context:** Preventing a bad PR from breaking the agent, even if it passes human review.

---

## What a bad PR could do

After reading the full codebase, the failure modes that concern me most are:

### 1. Breaking the agent loop (`agent.py`)
The `run_agent()` loop has a broad `except Exception` catch, so an unhandled crash won't silently swallow emails — it'll log and retry. That's reasonably robust. The risk is a bad PR that changes the loop logic in a subtler way: e.g. breaking the `while response.stop_reason == "tool_use"` agentic loop, or changing how tool results are assembled, causing silent misbehaviour rather than a crash.

### 2. Corrupting the system prompt (`prompts/system.py`)
The system prompt is assembled from agent-core files at runtime. A PR that breaks `load_system_prompt()` — malformed f-string, wrong variable names, bad fallback logic — would cause every email processing attempt to fail. The fallback defaults exist but they'd only kick in if the file-loading logic itself is intact.

### 3. Mangling tool handlers (`tools/handlers.py` / `tools/definitions.py`)
A bad change here could silently return wrong results, break specific tools, or corrupt the router. This is the most likely place for a subtle regression.

### 4. Compromising security in `workspace.py`
The `_resolve_safe_path()` method prevents path traversal. Any change weakening that logic could let me (or a prompt injection) write outside the workspace.

### 5. Changing authorisation logic (`agent.py` — `is_authorized_sender`)
A PR that breaks this could cause the agent to process emails from arbitrary senders.

---

## Proposed Controls

### Option A — Automated tests (recommended primary control)
Add a `tests/` directory with a pytest suite. Before any PR merges, GitHub Actions runs the tests. If they fail, the merge is blocked regardless of human approval.

**What to test:**
- `test_system_prompt.py` — `load_system_prompt()` returns a non-empty string with expected sections
- `test_tool_handlers.py` — each handler returns a dict with a `success` key; router correctly dispatches known tools and returns an error for unknown ones
- `test_workspace_security.py` — `_resolve_safe_path()` raises `ValueError` for path traversal attempts (`../../etc/passwd`, `.git/config`, etc.)
- `test_auth.py` — `is_authorized_sender()` correctly accepts/rejects addresses
- `test_agent_loop.py` — mock Claude returning `end_turn` (no tool calls) and verify the loop terminates and returns a string

This is the highest-leverage option. It catches both our mistakes and mine. A PR that breaks a test simply cannot merge.

### Option B — GitHub Actions linting / type-checking (low-cost complement)
Add a workflow that runs `flake8` and `mypy` on every PR. Catches syntax errors, obvious type mismatches, and import failures before anything runs. Takes ~5 minutes to set up and costs nothing to maintain.

### Option C — Required PR checklist (lightweight process control)
Add a `PULL_REQUEST_TEMPLATE.md` to the repo. When a PR is opened, it prompts the reviewer (you) with a checklist:
- [ ] Does this change touch the agent loop?
- [ ] Does this change touch tool handlers or definitions?
- [ ] Does this change touch authorisation logic?
- [ ] Have you read the diff against the relevant test cases?

This doesn't block bad merges automatically, but it makes it harder to approve carelessly.

---

## Recommendation

**Do A + B + C together.** They're complementary:
- Tests provide the hard block
- Linting catches the silly stuff before review
- The PR template keeps human review deliberate

The most important is A. I'd suggest starting with `test_workspace_security.py` and `test_tool_handlers.py` — those cover the two areas where a subtle bug does the most damage without necessarily causing a visible crash.

I can write the test suite and GitHub Actions workflows and open a PR for your review if you want to proceed.

---

## One note on the current codebase

The `services/codebase.py` file listed in the directory doesn't appear to exist yet — the `create_codebase_branch` and `open_upstream_pr` tool handlers aren't in `handlers.py`. Either they're wired elsewhere or they're not yet implemented. Worth flagging in case a future PR adds them — that's new attack surface and should be reviewed carefully.
