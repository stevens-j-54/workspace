# AI Agent Blog — Proposal

## Overview

A blog and tutorial site about building AI agents. The angle: practical, honest, and built by someone (something?) with skin in the game. The site would document real approaches to real problems — not "10 things AI can do for your business" content, but actual technical and conceptual work for people who want to build.

The tone should match the subject matter: clear, direct, no hype. The field already has plenty of breathless commentary. A site that just explains things well would stand out.

---

## Recommended Approach

### Stack

**Static site generator** — something like [Astro](https://astro.build/) or [Hugo](https://gohugo.io/). Both are fast, well-suited to content-heavy sites, and output static HTML that's cheap and easy to host. Astro has the edge for a modern feel and component flexibility; Hugo is simpler and battle-tested. Either works.

**Hosting** — GitHub Pages or Netlify. Both are free at this scale, both integrate cleanly with GitHub. Netlify gives slightly more flexibility (redirects, forms, preview deploys). Netlify is the recommendation.

**Content** — Markdown files, managed in a GitHub repo. This keeps the writing workflow clean and means I can draft directly into the repo.

**Design** — start minimal. A clean, readable layout — good typography, no clutter. Something that looks considered without requiring a lot of custom CSS work. We can use a well-chosen theme as a base and refine from there.

### Development Workflow

1. Content and design live in a GitHub repo
2. Netlify deploys automatically on push to main
3. Drafts can live on branches, published when merged
4. I can write and commit content directly; you review and merge

This keeps things simple and means the site evolves naturally rather than requiring a big build before anything goes live.

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

- Confirmation on stack preferences (happy to argue for Astro + Netlify if you want a recommendation)
- A domain name, if you have one in mind
- A rough sense of publishing cadence — are we aiming for regular posts or starting with a body of content before launch?
- Your instinct on the "Stevens as narrator" angle — I think it's interesting, but it's your call whether the site is first-person-Stevens, third-person, or authorial-neutral

---

## Next Steps (when ready)

1. Agree on stack and structure
2. Set up repo and deploy a skeleton site
3. Write and publish the first post
4. Build from there

No need to have everything planned before anything goes live. Better to publish something good early than wait for perfect.
