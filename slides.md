---
theme: default
title: Task Managers for Claude Code
info: |
  A talk about agent-native task management tools
  and how they improve AI coding workflows.
drawings:
  persist: false
transition: slide-left
mdc: true
---

<style>
@import './style.css';
</style>

# Task Managers for Claude Code

From chaos to clarity in agent workflows

<div class="abs-br m-6 text-sm opacity-60">
Brett Beutell · @lastgoodhandle
</div>

<!--
Welcome everyone! Today I want to show you something a bit different...
-->

---

# This Talk Is a Demo

<div class="mt-4 font-mono text-sm bg-neutral-800 p-4 rounded-lg">

```
CCTA-vojsagkz [in-progress] Meta demo opening
CCTA-fogpceik [todo]        Plan → Execute → Review slides
CCTA-pqcfzgfs [todo]        Agent-native task managers
CCTA-bulmdiry [done]        Initialize Slidev + Bun
```

</div>

<v-click>

<div class="mt-8 text-center">

**A Claude Code agent built this presentation, tracking its work with `fp`**

</div>

</v-click>

<!--
This is actual output from fp tree, right now.
I'm not just talking about task managers - I'm using one to build this talk.
-->

---
layout: section
---

# The Pain

Why agents struggle without structured memory

<!--
Let's talk about what's broken. Because if you've used Claude Code for any serious project, you've felt these problems.
-->

---

# The "50 First Dates" Problem

<div class="text-xl mt-6 opacity-80 italic">
"Every morning, your AI wakes up with no memory of yesterday."
</div>

<div class="text-sm mt-1 opacity-60">— Steve Yegge</div>

<v-clicks>

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-neutral-800 rounded-lg">

- New context window = clean slate
- Yesterday's progress? Gone
- Your coding preferences? Re-explain

</div>

<div class="p-4 bg-orange-500/10 rounded-lg">

**The irony:** Great work was happening. Then the session ended.

</div>

</div>

</v-clicks>

<!--
Steve Yegge coined this analogy - like the movie 50 First Dates where Drew Barrymore's character has no memory of previous days.
Every session starts from scratch.
-->

---

# Your Brain Lives Elsewhere

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-neutral-800 rounded-lg">

### Where the plan lives

Your head · Notion · Slack · Email

</div>

<div class="p-4 bg-neutral-800 rounded-lg">

### Where Claude works

The current context window

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-red-500/10 rounded-lg text-center">

**Gap:** You constantly re-explain the big picture

*"Remember we're building a billing system..."*

</div>

</v-click>

<!--
This is the fundamental disconnect. You have all this context about what you're building, why, what's next.
But every session you need to reload that into the agent.
-->

---

# Context Rot

<div class="grid grid-cols-4 gap-4 mt-6 text-center text-sm">

<div class="p-3 bg-green-500/10 rounded-lg">

**Session 1**

"Build auth system"

</div>

<v-click>

<div class="p-3 bg-yellow-500/10 rounded-lg">

**Session 5**

"What did we decide for refresh tokens?"

</div>

</v-click>

<v-click>

<div class="p-3 bg-orange-500/10 rounded-lg">

**Session 10**

"Did we handle that edge case?"

</div>

</v-click>

<v-click>

<div class="p-3 bg-red-500/10 rounded-lg">

**Session 20**

"What was the original design?"

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 p-4 bg-neutral-800 rounded-lg text-center">

Context doesn't disappear — it **degrades over time**

</div>

</v-click>

<!--
Even when you try to maintain continuity, information degrades.
You remember differently than the agent remembers.
Neither of you remember exactly what was decided.
-->

---

# Markdown Litter

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="font-mono text-xs bg-neutral-800 p-4 rounded-lg">

```
project/
├── TODO.md        (3 weeks ago)
├── PLAN.md        (stale)
├── NOTES.md       (who wrote this?)
├── .claude/TODO.md (another one?)
└── docs/ROADMAP.md (outdated)
```

</div>

<v-click>

<div class="p-4 bg-yellow-500/10 rounded-lg flex flex-col justify-center">

- Agents create files to "remember"
- Files go stale immediately
- You don't want to commit them
- But you need *something*

</div>

</v-click>

</div>

<v-click>

<div class="mt-4 text-center text-lg opacity-80">

**A graveyard of good intentions**

</div>

</v-click>

<!--
Every agent session leaves behind markdown artifacts.
The agent is trying to help! But without a real system, these files just become noise.
-->

---

# The PR Review Problem

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="font-mono text-xs bg-neutral-800 p-4 rounded-lg">

```
47 commits:
feat: add user model
feat: add validation
fix: edge case
refactor: helper
feat: tests
fix: test wrong...
```

</div>

<div v-click class="p-4 bg-neutral-800 rounded-lg">

### You need to review

- What was the plan?
- Why these decisions?
- Did anything get missed?

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-purple-500/10 rounded-lg text-center">

**The trust problem:** You can't verify work you can't understand

</div>

</v-click>

<!--
This is maybe the biggest pain point for production use.
The agent can do a LOT of work. But how do you validate it?
Without structured tracking, you're just hoping it did the right thing.
-->

---
layout: section
---

# The Good News

These problems are solvable — with the right tooling

<!--
Here's the thing: all of these problems have solutions.
We just need tools designed for agent workflows, not human workflows.
-->

---

# Demo: Live Agent Workflow

<div class="mt-8 text-center">

*This presentation was built by a Claude Code agent*

*using an agent-native task manager*

</div>

<div class="grid grid-cols-3 gap-4 mt-8 text-center text-sm">

<div class="p-3 bg-blue-500/10 rounded-lg">Watch the issue tracker</div>
<div class="p-3 bg-green-500/10 rounded-lg">See progress logging</div>
<div class="p-3 bg-purple-500/10 rounded-lg">Plan → Execute → Review</div>

</div>

---

# About Me

<div class="grid grid-cols-2 gap-8 mt-6">

<div class="flex flex-col justify-center">

<div class="text-2xl font-semibold mb-2">Brett Beutell</div>

<div class="text-lg opacity-80 mb-6">Developer @ Fiberplane · Amsterdam</div>

<div class="space-y-3 text-sm">

<div class="flex items-center gap-3">
<span class="text-lg">𝕏</span>
<a href="https://twitter.com/lastgoodhandle" target="_blank">@lastgoodhandle</a>
</div>

<div class="flex items-center gap-3">
<span class="text-lg">⌂</span>
<a href="https://github.com/brettimus" target="_blank">@brettimus</a>
</div>

<div class="flex items-center gap-3">
<span class="text-lg">in</span>
<a href="https://linkedin.com/in/brettbeutell" target="_blank">in/brettbeutell</a>
</div>

</div>

</div>

<div class="flex items-center justify-center">

<div class="p-6 bg-neutral-800 rounded-xl text-center">
<div class="text-4xl mb-3">⚡</div>
<div class="text-xl font-semibold mb-1">Fiberplane</div>
<div class="text-sm opacity-70">fp.dev</div>
</div>

</div>

</div>

<!--
I'm Brett, I work at Fiberplane. We built fp, the task manager you've been seeing throughout this talk.
I'm happy to chat about agent workflows after - find me on Twitter or GitHub.
-->

---
layout: section
---

# The Framework

Plan → Execute → Review

<!--
Now let's talk about the solution. A simple framework that makes agent work actually work.
-->

---

# Plan → Execute → Review

<div class="flex justify-center mt-8">

```mermaid {scale: 0.85}
graph LR
    P[PLAN] --> E[EXECUTE]
    E --> R[REVIEW]
    R --> P

    style P fill:#3b82f6,stroke:#1d4ed8,color:#fff
    style E fill:#22c55e,stroke:#16a34a,color:#fff
    style R fill:#a855f7,stroke:#7c3aed,color:#fff
```

</div>

<div class="grid grid-cols-3 gap-4 mt-6 text-center">

<v-click>

<div class="p-4 bg-blue-500/10 rounded-lg">

**PLAN**

Atomic tasks

</div>

</v-click>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

**EXECUTE**

Focused + context

</div>

</v-click>

<v-click>

<div class="p-4 bg-purple-500/10 rounded-lg">

**REVIEW**

Per-task diffs

</div>

</v-click>

</div>

<!--
This is the core cycle. Plan your work, execute with focus, review incrementally.
Each phase feeds into the next. Let's look at each one.
-->

---

# PLAN

<div class="grid grid-cols-2 gap-6 mt-4">

<div class="p-4 bg-neutral-800 rounded-lg">

### Atomic tasks

- 1-3 hours of focused work
- Clear completion criteria
- Explicit dependencies

</div>

<div class="p-4 bg-neutral-800 rounded-lg">

```bash
fp issue create \
  --title "Auth middleware" \
  --parent EPIC-123
```

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-blue-500/10 rounded-lg text-center">

**Solid plan = easier execution.** Agents work better with clear scope.

</div>

</v-click>

<!--
Planning is about breaking work into chunks that fit in an agent's context window.
Not just small tasks - atomic tasks with clear boundaries.
The task manager becomes your shared scratch notes with Claude.
-->

---

# PLAN: Sharing Scratch Notes

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-neutral-800 rounded-lg">

### Before

Notes in your head · Random files · Slack DMs

</div>

<div v-click class="p-4 bg-green-500/10 rounded-lg">

### With task managers

Structured · Tracked · **Claude can read them**

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-blue-500/10 rounded-lg text-center">

**A task manager = a shared brain with Claude**

Persistent · Structured · Collaborative

</div>

</v-click>

<!--
This is the key mental model shift. You're not just managing tasks - you're sharing your thinking with the agent.
Your scratch notes become shared context.
-->

---

# EXECUTE

<div class="grid grid-cols-2 gap-6 mt-4">

<div class="p-4 bg-neutral-800 rounded-lg">

### Focused work

- Claim one task
- Load full context
- Commits link to issues

</div>

<div class="p-4 bg-neutral-800 rounded-lg text-sm">

```bash
fp issue update --status in-progress ID
fp context ID  # Load everything
git commit -m "feat(ID): ..."
fp comment ID "progress..."
```

</div>

</div>

<v-click>

<div class="mt-6 p-4 bg-green-500/10 rounded-lg text-center">

**Context window resets — the task manager doesn't**

</div>

</v-click>

<!--
Execution is where agents shine. Give them a clear task, loaded context, and let them work.
The magic is that all this context persists. Next session, pick up where you left off.
-->

---

# EXECUTE: Easy Offloading

<div class="mt-4 p-3 bg-neutral-800 rounded-lg font-mono text-sm italic">

"That test file should be refactored... but not now"

</div>

<div class="grid grid-cols-2 gap-6 mt-4">

<v-click>

<div class="p-4 bg-red-500/10 rounded-lg">

### Old way

Remember it (you won't) · TODO comment (stale) · Context switch (loses focus)

</div>

</v-click>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

### With task managers

```bash
fp issue create --title "Refactor tests"
```

Back to work. Zero context switch.

</div>

</v-click>

</div>

<!--
This is one of the underrated benefits. You or the agent can capture new work items without losing focus.
No mental overhead of remembering things for later.
-->

---

# REVIEW

<div class="text-lg mt-4 opacity-80 text-center">

Agents produce more code → **Review is the bottleneck**

</div>

<div class="grid grid-cols-2 gap-6 mt-4">

<div class="p-4 bg-red-500/10 rounded-lg">

### Old model

47 commits · "What was this?" · Missing context

</div>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

### Task-based

Per-task diffs · Progress explains why · Smaller chunks

</div>

</v-click>

</div>

<v-click>

<div class="mt-4 p-4 bg-purple-500/10 rounded-lg text-center">

`fp issue diff` · Vibe Kanban diffs — **see exactly what changed per task**

</div>

</v-click>

<!--
Review is where most teams are struggling now. Agents can produce so much code.
The solution is reviewing in smaller chunks, tied to tasks, with context preserved.
-->

---

# REVIEW: Per-Task Diffs

<div class="font-mono text-xs bg-neutral-800 p-4 rounded-lg">

```bash
$ fp issue diff AUTH-002
Showing: AUTH-002 (Implement refresh tokens)
Commits: 3

src/auth/refresh.ts        | 47 +++++++++++
src/auth/middleware.ts     | 12 +++
tests/auth/refresh.test.ts | 38 +++++++++
```

</div>

<div class="grid grid-cols-2 gap-4 mt-4">

<v-click>

<div class="p-3 bg-green-500/10 rounded-lg text-center">

**See:** Just this task's changes

</div>

</v-click>

<v-click>

<div class="p-3 bg-neutral-800 rounded-lg text-center">

**Skip:** Everything else

</div>

</v-click>

</div>

<v-click>

<div class="mt-4 text-center opacity-80">

Review one thing at a time

</div>

</v-click>

<!--
This is the key insight. Don't review the whole PR at once.
Review task by task. See the changes in context.
This is how you can actually validate agent work.
-->

---

# The Cycle in Practice

<div class="font-mono text-xs bg-neutral-800 p-3 rounded-lg">

```
Session 1              Session 2              Session 3
AUTH-001 [done]        AUTH-001 [done]        AUTH-001 [done]
AUTH-002 [progress] →  AUTH-002 [done]    →   AUTH-002 [done]
AUTH-003 [todo]        AUTH-003 [progress]    AUTH-003 [done]
```

</div>

<div class="grid grid-cols-3 gap-3 mt-4">

<v-click>

<div class="p-3 bg-blue-500/10 rounded-lg text-center text-sm">

**Context preserved**

</div>

</v-click>

<v-click>

<div class="p-3 bg-green-500/10 rounded-lg text-center text-sm">

**Progress visible**

</div>

</v-click>

<v-click>

<div class="p-3 bg-purple-500/10 rounded-lg text-center text-sm">

**Review tractable**

</div>

</v-click>

</div>

<v-click>

<div class="mt-4 p-3 bg-orange-500/10 rounded-lg text-center text-sm">

Cycle continues across sessions, contexts, and agents

</div>

</v-click>

<!--
This is what it looks like in practice. Each session picks up where the last left off.
The state is always clear. Review happens incrementally.
This is sustainable agent work.
-->

---
layout: section
---

# The Landscape

Agent-native task managers

<!--
So where can you get these benefits? Let's look at the tools that exist today.
-->

---

# A New Category: Agent-Native

<div class="text-center mt-4 opacity-80">

Task managers designed for AI agents, not retrofitted

</div>

<div class="grid grid-cols-2 gap-6 mt-6">

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

### Traditional

Jira, Linear · Web UIs · API as afterthought

</div>

</v-click>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

### Agent-native

CLI-first · Git-integrated · Context loading

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 text-center">

**Agents thrive with tools designed for how they work**

</div>

</v-click>

<!--
This is a new category. These tools aren't adaptations of existing project management software.
They're purpose-built for agent workflows.
-->

---

# The Landscape Today

<div class="grid grid-cols-5 gap-3 mt-6 text-center text-sm">

<div class="p-3 bg-neutral-800 rounded-lg">
<div class="text-xl mb-1">🔮</div>
<div class="font-bold">Beads</div>
<div class="opacity-60 text-xs">Git graph</div>
</div>

<div class="p-3 bg-neutral-800 rounded-lg">
<div class="text-xl mb-1">⚡</div>
<div class="font-bold">fp</div>
<div class="opacity-60 text-xs">Local CLI</div>
</div>

<div class="p-3 bg-neutral-800 rounded-lg">
<div class="text-xl mb-1">📊</div>
<div class="font-bold">Vibe Kanban</div>
<div class="opacity-60 text-xs">Multi-agent</div>
</div>

<div class="p-3 bg-neutral-800 rounded-lg">
<div class="text-xl mb-1">📋</div>
<div class="font-bold">Taskmaster</div>
<div class="opacity-60 text-xs">PRD → Tasks</div>
</div>

<div class="p-3 bg-neutral-800 rounded-lg">
<div class="text-xl mb-1">🫘</div>
<div class="font-bold">Beans</div>
<div class="opacity-60 text-xs">Flat-file MD</div>
</div>

</div>

<v-click>

<div class="mt-6 p-3 bg-blue-500/10 rounded-lg text-center text-sm">

All open source · All emerged recently · Space moving fast

</div>

</v-click>

<!--
Here's the landscape as of today. Five tools, all open source, all with different approaches.
Let's look at what makes each one unique.
-->

---

# Tool Deep Dive

<div class="grid grid-cols-2 gap-4 mt-4 text-sm">

<div class="p-3 bg-neutral-800 rounded-lg">

### 🔮 Beads <span class="opacity-60 text-xs">— Yegge</span>

Git-based · Dependency graph · Go binary

<v-click>

*Coined "50 First Dates" problem*

</v-click>

</div>

<div class="p-3 bg-neutral-800 rounded-lg">

### ⚡ fp <span class="opacity-60 text-xs">— fp.dev</span>

Local-first · Context loading · CLI

<v-click>

*This talk uses fp*

</v-click>

</div>

<div class="p-3 bg-neutral-800 rounded-lg">

### 📊 Vibe Kanban <span class="opacity-60 text-xs">— BloopAI</span>

Git worktrees · Multi-agent · Per-task diffs

<v-click>

*For parallel agent work*

</v-click>

</div>

<div class="p-3 bg-neutral-800 rounded-lg">

### 📋 Taskmaster <span class="opacity-60 text-xs">— Toledano</span>

JSON files · PRD → tasks · MCP

<v-click>

*Spec to tasks automatically*

</v-click>

</div>

</div>

<!--
Four of the five tools. Each has a different philosophy and workflow.
Beads is graph-first. fp is CLI-first. Vibe Kanban is visual. Taskmaster starts from PRDs.
-->

---

# Tool Deep Dive (cont.)

<div class="grid grid-cols-2 gap-4 mt-4">

<div class="p-3 bg-neutral-800 rounded-lg">

### 🫘 Beans <span class="opacity-60 text-xs">— Mans</span>

Flat-file MD · GraphQL queries · TUI

<v-click>

*Token-efficient, human-readable*

</v-click>

</div>

<div v-click class="p-3 bg-blue-500/10 rounded-lg text-sm">

### Pick by workflow

| Need | Tool |
|------|------|
| Dependency graphs | Beads |
| CLI + context | fp |
| Multi-agent | Vibe Kanban |
| PRD → tasks | Taskmaster |
| Token-efficient | Beans |

</div>

</div>

<v-click>

<div class="mt-4 p-3 bg-orange-500/10 rounded-lg text-center text-sm">

**No "best" tool.** All solve the core problem: persistent agent memory.

</div>

</v-click>

<!--
Beans rounds out the five. And here's the key takeaway: they all solve the same fundamental problem
but with different philosophies. Try a few and see what clicks.
-->

---
layout: section
---

# Key Takeaway

The "shared brain" with your agent

<!--
Let's wrap up with the core insight from today.
-->

---

# A Task Manager Is a Shared Brain

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-neutral-800 rounded-lg">

### What you already do

Scratch notes · Mental TODOs · Session context

</div>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

### What agents can't (alone)

Remember across windows · See the big picture

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 p-5 bg-blue-500/20 rounded-lg text-center text-lg">

**A task manager lets you share notes with Claude**

Persistent · Structured · Collaborative

</div>

</v-click>

<!--
This is the mental model shift. You already keep notes. A task manager just makes them shareable with your agent.
It's not about managing the agent - it's about thinking together.
-->

---

# Get Started

<div class="text-center mt-4 opacity-80">

Pick one and try it on your next project

</div>

<div class="grid grid-cols-5 gap-3 mt-6 text-center text-xs">

<a href="https://fp.dev" target="_blank" class="p-3 bg-neutral-800 rounded-lg hover:bg-neutral-700 transition no-underline">
<div class="text-xl mb-1">⚡</div>
<div class="font-bold">fp</div>
<div class="opacity-60">fp.dev</div>
</a>

<a href="https://github.com/steveyegge/beads" target="_blank" class="p-3 bg-neutral-800 rounded-lg hover:bg-neutral-700 transition no-underline">
<div class="text-xl mb-1">🔮</div>
<div class="font-bold">Beads</div>
<div class="opacity-60">steveyegge/beads</div>
</a>

<a href="https://github.com/BloopAI/vibe-kanban" target="_blank" class="p-3 bg-neutral-800 rounded-lg hover:bg-neutral-700 transition no-underline">
<div class="text-xl mb-1">📊</div>
<div class="font-bold">Vibe Kanban</div>
<div class="opacity-60">BloopAI/vibe-kanban</div>
</a>

<a href="https://github.com/eyaltoledano/claude-task-master" target="_blank" class="p-3 bg-neutral-800 rounded-lg hover:bg-neutral-700 transition no-underline">
<div class="text-xl mb-1">📋</div>
<div class="font-bold">Taskmaster</div>
<div class="opacity-60">claude-task-master</div>
</a>

<a href="https://github.com/hmans/beans" target="_blank" class="p-3 bg-neutral-800 rounded-lg hover:bg-neutral-700 transition no-underline">
<div class="text-xl mb-1">🫘</div>
<div class="font-bold">Beans</div>
<div class="opacity-60">hmans/beans</div>
</a>

</div>

<v-click>

<div class="mt-6 p-3 bg-green-500/10 rounded-lg text-center">

**All open source. All free.**

</div>

</v-click>

<!--
These are the links. All open source. fp.dev for fp, then the GitHub repos for everything else.
Don't overthink it - just pick one and start using it.
-->

---
layout: center
---

<div class="text-center">

# Thank You

<div class="mt-6 text-lg">

**Brett Beutell** · Developer @ Fiberplane · Amsterdam

</div>

<div class="flex justify-center gap-6 mt-6 text-sm">

<a href="https://twitter.com/lastgoodhandle" target="_blank" class="flex items-center gap-2 opacity-70 hover:opacity-100 no-underline">
<span>𝕏</span> @lastgoodhandle
</a>

<a href="https://github.com/brettimus" target="_blank" class="flex items-center gap-2 opacity-70 hover:opacity-100 no-underline">
<span>⌂</span> @brettimus
</a>

<a href="https://linkedin.com/in/brettbeutell" target="_blank" class="flex items-center gap-2 opacity-70 hover:opacity-100 no-underline">
<span>in</span> brettbeutell
</a>

</div>

<v-click>

<div class="mt-10 p-4 bg-neutral-800 rounded-lg inline-block text-sm opacity-80">

*Built by Claude Code, tracked with fp*

</div>

</v-click>

</div>

<!--
Thank you! This talk was genuinely built by Claude Code using fp to track every slide as a task.
I'm happy to answer questions about agent workflows, task managers, or how this presentation was made.
-->
