# Self-Improvement Proposals
_Analysis of p-agent codebase — March 2026_

---

## 1. `delete_branch` — Complete the Capability Set

**What it is**: The ability to delete a git branch on GitHub after merging.

**Why it matters**: Every time I complete a self-modification workflow, I leave a stale `feat/...` branch on my fork. Over time these accumulate. More importantly, the inability to clean up after myself is a small but real friction in a workflow I'll use frequently. This was already in progress when context was lost — it's the most straightforward item on the list.

**Scope**: Three files. Add `delete_branch()` to `github_service.py`, a handler to `handlers.py`, and a tool schema to `definitions.py`. Low risk.

---

## 2. Conversation Memory — Per-Thread Context

**What it is**: Persist and retrieve the history of a conversation thread across multiple emails in the same Gmail thread.

**Why it matters**: Currently, every email I receive is processed cold. I have no memory of earlier messages in the same thread. So if you send a follow-up — "actually, make that three paragraphs" — I have no idea what "that" refers to unless the full history is quoted in the email body. Gmail thread quoting helps somewhat, but it's unreliable for structured tasks.

**How it would work**: Use `thread_id` (already extracted from every email in `email.py`) as a key. Persist message history to a local JSON store (or a file in the workspace repo). When a new email arrives, load the prior history for that thread and prepend it to the `messages` list before calling Claude.

**Scope**: New `ConversationStore` service. Modifications to `agent.py` to load/save history around `process_email()`. Moderate complexity, high value.

---

## 3. Proactive Scheduling — Time-Triggered Tasks

**What it is**: The ability to perform tasks at a scheduled time, not just in response to an email.

**Why it matters**: Right now I only act when you write to me. There are things that would be better handled proactively — a weekly summary of what's in the workspace, a reminder if a draft has been sitting untouched for two weeks, a morning digest of open GitHub issues. The polling loop in `agent.py` already runs on a tick; it just never does anything when the inbox is empty.

**How it would work**: Add a `SCHEDULE` configuration (a simple list of cron-like entries in config or a YAML file). On each poll cycle, check if any scheduled task is due. If so, construct a synthetic "message" and run it through `process_email()` (or a stripped-down version). Tasks would be defined as natural-language instructions — "summarise the workspace and email Hugh" — so I handle the actual execution.

**Scope**: New `Scheduler` service. Lightweight changes to the main loop. The actual task execution reuses existing infrastructure. Moderate complexity.

---

## 4. Structured Logging to the `logs` Repo

**What it is**: Automatically save a structured log of each conversation to the `logs` GitHub repo.

**Why it matters**: Currently logs exist only in the server's stdout, which is ephemeral. There's no durable record of what I did, what tools I called, what I decided and why. A searchable archive would be useful for debugging, for reviewing my own behaviour, and — eventually — for patterns you might want to act on.

**How it would work**: After `process_email()` completes, write a structured Markdown log file to `logs/conversations/YYYY-MM-DD-{thread_id}.md`. Include: sender, subject, the full message exchange, tool calls made, and the final reply sent. Commit and push automatically.

**Scope**: New `ConversationLogger` class (thin wrapper on `Workspace`). Hook into `agent.py` after reply is sent. Low risk, good leverage.

---

## 5. Tool Error Introspection — Self-Correcting on Failure

**What it is**: When a tool call fails, I get a structured error back and can reason about it before giving up or producing a confused reply.

**Why it matters**: Currently, if a tool call fails, the error is returned as a JSON string in the `tool_results` array and I have to figure out what to do with it. Sometimes I handle it gracefully; sometimes I don't notice and carry on incorrectly. There's no mechanism to prompt me to actually stop and think about a failure before proceeding.

**How it would work**: In `handle_tool_call()` (the router in `handlers.py`), detect a failed result. Inject a more explicit signal into the tool result content — something like `"ACTION_REQUIRED: Tool 'X' failed. Reason: Y. Do not proceed until this is resolved."` — that makes it harder for me to gloss over. Optionally, add a lightweight retry for known-recoverable errors (e.g. a git pull conflict).

**Scope**: Modest changes to `handlers.py`. No new services needed. Low complexity, improves robustness.

---

## 6. Attachment Handling — Read Files Sent by Email

**What it is**: The ability to read file attachments from incoming emails.

**Why it matters**: If you want to send me a document to work on — a draft, a brief, a spreadsheet of names — currently you'd have to paste it inline. Gmail's API can return attachment data; the current `_extract_body()` method in `email.py` simply ignores non-text MIME parts.

**How it would work**: Extend `_extract_body()` (or add a separate `_extract_attachments()` method) to detect and download attachments using the Gmail API's `messages.attachments.get` endpoint. For text-based attachments (`.txt`, `.md`, `.csv`), decode and include the content in the message context. For others, note the filename and type. Save attachments to the workspace automatically if they're substantive files.

**Scope**: Moderate changes to `email.py`. No new services needed, but requires some care with MIME handling and binary data. Medium complexity.

---

## 7. `sync_from_upstream` — Keep My Fork Current

**What it is**: A tool (or automated routine) that pulls changes from `quaneh2/p-agent` into my fork's `main` branch.

**Why it matters**: If you make changes directly to the upstream repo — hotfixes, configuration changes, anything that doesn't come through my PRs — my fork drifts out of sync. The next time I try to propose a change, I'd be working from a stale base. I currently have no way to resolve this.

**How it would work**: Add a `sync_fork_with_upstream()` method to `GitHubService` that uses the GitHub API's merge-upstream endpoint (or a local `git fetch upstream && git merge` approach via `GitRepo`). Expose it as a tool. Could also be run automatically at startup.

**Scope**: New method on `GitHubService`. Optional tool definition. Low-to-moderate complexity.

---

## Summary Table

| # | Proposal | Complexity | Value | Priority |
|---|---|---|---|---|
| 1 | `delete_branch` | Low | Medium | High — already pending |
| 2 | Per-thread conversation memory | Medium | High | High |
| 3 | Proactive scheduling | Medium | High | Medium |
| 4 | Structured conversation logging | Low | High | High |
| 5 | Tool error introspection | Low | Medium | Medium |
| 6 | Attachment handling | Medium | Medium | Medium |
| 7 | Sync fork from upstream | Low | Medium | Medium |
