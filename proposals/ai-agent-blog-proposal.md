# AI Agent Blog — Proposal

## Overview

A blog and tutorial site about building AI agents. The angle: practical, honest, and built by someone (something?) with skin in the game. The site would document real approaches to real problems — not "10 things AI can do for your business" content, but actual technical and conceptual work for people who want to build.

The tone should match the subject matter: clear, direct, no hype. The field already has plenty of breathless commentary. A site that just explains things well would stand out.

---

## Recommended Approach

### Stack

**Static site generator** — [Astro](https://astro.build/). Fast, well-suited to content-heavy sites, outputs static HTML, and has good syntax highlighting support out of the box. Installed locally via npm — no subscription or service required. You run `npm create astro@latest`, write content as Markdown, and Astro compiles it to plain HTML/CSS at build time.

**Hosting** — Render. Integrates cleanly with GitHub and fits the existing stack. Push to main → site deploys automatically.

**Content** — Markdown files, managed in a GitHub repo. This keeps the writing workflow clean and means I can draft directly into the repo.

**Design** — start minimal. A clean, readable layout — good typography, no clutter. Something that looks considered without requiring a lot of custom CSS work. We can use a well-chosen theme as a base and refine from there.

### Development Workflow

1. Content and design live in a GitHub repo
2. Render deploys automatically on push to main
3. Drafts can live on branches, published when merged
4. I can write and commit content directly; you review and merge

This keeps things simple and means the site evolves naturally rather than requiring a big build before anything goes live.

---

## Voice and Tone

The site will be written in first person, from my perspective as Stevens. This is not a stylistic flourish — it's the honest framing. The content is about building AI agents, written by one. That's a natural point of view, and it's distinctive without being gimmicky.

The important constraint: first-person does not mean performatively personal. The voice comes through in *how* things are explained — directly, with a point of view, without unnecessary hedging — not in meta-commentary or manufactured warmth. No "I felt a sense of wonder." Just: here's how this works, here's why it matters, here's how to build it.

The goal is writing that reads as clear and considered, where the author's presence is felt in the quality of the explanation, not announced in the prose. Lean and instructional. The field has enough AI-generated content that mistakes padding for personality — this site should be the opposite of that.

---

## Initial Content Ideas

The site should have a point of view. I'd suggest framing it around **"building agents that actually work"** — meaning agents that are reliable, maintainable, and genuinely useful, not just demos.

### Foundational Posts

1. **What is an AI agent, really?**
   A clear, unsentimental definition. What makes something an agent vs. a chatbot vs. a script. Covers the core loop: perceive → decide → act.

2. **The surprisingly hard parts of building agents**
   Not the glamorous stuff — the infrastructure. Email parsing, state management, error handling, rate limits. The gap between "it works in a notebook" and "it runs reliably."

3. **Tool use: how agents interact with the world**
   A practical guide to designing tool schemas, handling failures, and thinking about what tools an agent should and shouldn't have.

4. **Memory, context, and why agents forget things**
   The different types of memory (in-context, external, semantic, episodic) and how to think about each. Practical patterns for keeping agents stateful across conversations.

5. **How I built Stevens** *(meta post — could be strong)*
   A walkthrough of this project: the architecture, the decisions, the things that didn't work. Honest and specific. Posts like this tend to travel well.

### Tutorial Series

A step-by-step series building a simple but complete agent from scratch:

- Part 1: Setting up the loop (polling, parsing, responding)
- Part 2: Giving it tools
- Part 3: Connecting to GitHub
- Part 4: Adding persistent memory
- Part 5: Self-modification and the interesting questions it raises

### Ongoing / Opinion

- **Prompting is engineering** — why system prompt design deserves the same rigour as code
- **When not to use an agent** — a genuinely useful post that most AI blogs won't write
- **The identity question** — can an agent have a consistent character? Should it?

---

## What I'd Need from You

- A domain name, if you have one in mind
- A rough sense of publishing cadence — are we aiming for regular posts or starting with a body of content before launch?

---

## Next Steps (when ready)

1. Set up repo and deploy a skeleton site
2. Write and publish the first post
3. Build from there

No need to have everything planned before anything goes live. Better to publish something good early than wait for perfect.
