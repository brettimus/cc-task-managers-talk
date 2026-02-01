---
theme: default
title: Claude Really Wants a Task Manager
info: |
  A talk about agent-native task management tools
  and how they improve AI coding workflows.
favicon: https://fav.farm/🤖
drawings:
  persist: false
transition: slide-left
mdc: true
---

<style>
@import './style.css';
</style>

# Claude *Really* Wants a Task Manager

<div class="abs-br m-6 text-sm">
Brett Beutell · @lastgoodhandle
</div>

<!--
Welcome everyone! Today I want to show you something a bit different...
-->

---

# Claude can help you to help Claude

<div class="mt-12">

<div class="text-xl opacity-80 leading-relaxed max-w-2xl">

If you ask Claude to build a tool for itself to be more effective,

you will end up with a **lightweight task manager**.

</div>

</div>

<v-click>

<div class="mt-12 opacity-60">

There's a reason for that.

</div>

</v-click>

<!--
Claude can help you help Claude be more effective - and task management is what it wants.
It's not a coincidence - it's a necessity.
-->

---

# About Me

<div class="grid grid-cols-2 gap-8 mt-6">

<div class="flex flex-col justify-center">

<div class="text-2xl font-semibold mb-2">Brett Beutell</div>

<div class="text-lg opacity-80 mb-6">Engineering Lead @ Fiberplane · Amsterdam</div>

<div class="space-y-3 text-sm">

<div class="flex items-center gap-3">
<span class="text-lg w-5 text-center">𝕏</span>
<a href="https://twitter.com/lastgoodhandle" target="_blank">@lastgoodhandle</a>
</div>

<div class="flex items-center gap-3">
<mdi-github class="text-lg w-5 text-center" />
<a href="https://github.com/brettimus" target="_blank">@brettimus</a>
</div>

<div class="flex items-center gap-3">
<span class="text-lg w-5 text-center">in</span>
<a href="https://linkedin.com/in/brettbeutell" target="_blank">in/brettbeutell</a>
</div>

</div>

</div>

<div class="flex items-center justify-center">

<div class="p-6 bg-neutral-800 rounded-xl text-center">
<img src="/fiberplane-logo.svg" class="w-10 h-10 mx-auto mb-3 fp-logo-white" alt="Fiberplane" />
<div class="text-xl font-semibold mb-1">Fiberplane</div>
<a href="https://fp.dev" target="_blank" class="text-sm opacity-70 hover:opacity-100">fp.dev</a>
</div>

</div>

</div>

<!--
I'm Brett, I work at Fiberplane. We built fp, the task manager I'll be showing you today.
-->

---

# A Very Meta Demo

<div class="mt-8">

**A Claude Code agent built this presentation, tracking its work with `fp`**

</div>

<v-click>

<TerminalOutput title="fp tree">
  <TaskLine id="CCTA-vojsagkz" status="in-progress">Meta demo opening</TaskLine>
  <TaskLine id="CCTA-fogpceik" status="todo">Plan → Execute → Review slides</TaskLine>
  <TaskLine id="CCTA-pqcfzgfs" status="todo">Agent-native task managers</TaskLine>
  <TaskLine id="CCTA-bulmdiry" status="done">Initialize Slidev + Bun</TaskLine>
</TerminalOutput>

</v-click>

<!--
This is actual output from fp tree, right now.
I'm not just talking about task managers - I'm using one to build this talk.
-->

---
layout: section
---

<h1 class="!text-4xl">Ambitious work requires multiple Claude sessions</h1>

<!--
Let's start with the first problem you'll hit when doing real work with Claude Code.
-->

---

# Why Multiple Sessions?

<div class="grid grid-cols-3 gap-4 mt-6">

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Context is finite**

Performance degrades as you add more

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Compaction isn't great**

Getting better, but lossy

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Wrong turns happen**

Dead ends deserve documentation

</div>

</v-click>

</div>

<v-click>

<div class="mt-8 p-4 bg-amber-500/10 rounded-lg text-center">

**Any ambitious project spans multiple sessions**

</div>

</v-click>

<!--
Context windows are finite. Eventually you need to start fresh.
But how do you carry forward what you learned?
-->

---

# The Development Cycle

<CycleGraphic />

<v-click>

<div class="mt-4 text-center opacity-80">

The more capable Claude becomes, the more important **Planning** becomes — and the more difficult **Review** becomes

</div>

</v-click>

<v-click>

<div class="mt-4 text-center text-sm opacity-60">

We can't plan everything up front; often we need explorations and iterations

</div>

</v-click>

<!--
This is the development cycle. As Claude gets more capable, planning matters more and review gets harder.
And we can't plan everything upfront - we learn as we go.
-->

---

# Current Solutions

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-neutral-800 rounded-lg">

### SPEC files

Track goals across sessions

```
SPEC.md
├── Goals
├── Architecture decisions
└── Current status
```

</div>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

### Dev logs

Record design decisions and reasoning

```
DEV_LOG.md
├── 2024-01-15: Tried X, failed
├── 2024-01-16: Approach Y works
└── 2024-01-17: Refactored Z
```

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 text-center opacity-70">

These help... but they're not quite right

</div>

</v-click>

<!--
People have invented solutions. SPEC files, dev logs, context docs.
They work, to a point.
-->

---

# The Problems

<div class="grid grid-cols-2 gap-6 mt-6">

<v-click>

<div class="p-4 bg-rose-500/10 border border-rose-500/20 rounded-lg">

### Codebase clutter

- SPEC.md, PLAN.md, TODO.md, DEV_LOG.md
- Which one is current?
- Do you commit them?

</div>

</v-click>

<v-click>

<div class="p-4 bg-rose-500/10 border border-rose-500/20 rounded-lg">

### Lost explorations

- Failed approaches don't survive squash
- "Why didn't we do X?" - no record
- Reasoning evaporates

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 p-4 bg-amber-500/10 rounded-lg text-center">

**We need structured persistence, not scattered docs**

</div>

</v-click>

<!--
The core problem: these ad-hoc solutions don't scale.
They clutter your repo and still lose information.
-->

---
layout: section
---

<h1 class="!text-4xl">Reviewing massive Claude PRs is hard</h1>

<!--
The second problem hits when you need to verify what Claude actually built.
-->

---

# The Wall of Diffs

<div class="grid grid-cols-2 gap-6 mt-6">

<v-click>

<div class="p-4 bg-red-500/10 rounded-lg">

### Claude still makes mistakes

Opus 4.5 is good but it isn't perfect

- Doesn't delete dead code
- Creates unnecessary abstractions
- Cheats on tests (mocks everything)
- Misunderstands requirements

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

### Large changes lack review guidance

Most tools show a wall of diffs

```diff
+ 47 files changed
+ 3,847 insertions
+ 1,291 deletions
```

Good luck finding the bug.

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 p-4 bg-orange-500/10 rounded-lg text-center">

**You can't trust agent code you can't review**

</div>

</v-click>

<!--
Claude is good but not perfect. The problem is validating what it produced.
When you're staring at 47 changed files, how do you know what to check?
-->

---

# People are working on this

<div class="grid grid-cols-2 gap-6 mt-6">

<div class="p-4 bg-blue-500/10 rounded-lg">

### Approaches

- Narrative-based review
- Per-task diffs
- Structured commits (reasoning traces)

</div>

<div class="p-4 bg-neutral-800 rounded-lg">

### Resources

<div class="text-sm space-y-1 mt-2">

- <a href="https://linear.app/reviews" target="_blank">Linear Reviews</a>
- <a href="https://docs.devin.ai/work-with-devin/devin-review" target="_blank">Devin Review</a>
- <a href="https://cursor.com/blog/graphite" target="_blank">Graphite + Cursor</a>
- <a href="https://x.com/evanjconrad" target="_blank">@evanjconrad</a>
- <a href="https://x.com/benhylak" target="_blank">@benhylak</a>

</div>

</div>

</div>

<!--
This is genuinely an open problem. But the insight is: review by task, not by PR.
That's what task managers enable.
-->

---
layout: section
---

# What Task Managers Solve

<!--
Now let's look at what task managers actually provide.
-->

---

# Four Key Capabilities

<div class="grid grid-cols-2 gap-6 mt-6">

<v-click>

<div class="p-4 bg-blue-500/10 rounded-lg">

### External plan storage

Plans and subtasks persist longer than the 30-day .claude dir default

</div>

</v-click>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

### Record of Exploration

Document what you tried - including failures

</div>

</v-click>

<v-click>

<div class="p-4 bg-purple-500/10 rounded-lg">

### Clean context resets

Clear window, load next task's context

</div>

</v-click>

<v-click>

<div class="p-4 bg-orange-500/10 rounded-lg">

### Intent-to-code linking

Natural language intent tied to commits

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 text-center text-lg">

**These work together to create a shared brain with Claude**

</div>

</v-click>

<!--
Four capabilities that matter. External storage, exploration docs, clean resets, and intent linking.
Together they give your agent a memory that survives context windows.
-->

---

# Sharing Your Brain with Claude

<div class="mt-8">

<div class="text-xl opacity-80 leading-relaxed max-w-2xl">

You already do this while coding - jot down notes, file bugs for later, keep track of ideas

</div>

</div>

<v-click>

<div class="mt-8 p-4 bg-neutral-800 rounded-lg max-w-xl">

<div class="text-sm font-mono opacity-70 mb-2">// While implementing auth...</div>

"Oh, this error message is confusing - I'll file that for later"

</div>

</v-click>

<v-click>

<div class="mt-6 text-center opacity-70">

**Task managers give Claude the same ability to stay focused and capture context**

</div>

</v-click>

<!--
This is something we naturally do as humans - keep notes, file things for later.
Task managers extend this capability to Claude, letting it stay focused while not losing track of observations.
-->

---
layout: section
---

# What Solutions Exist

<!--
Let's look at what's out there for agent-native task management.
-->

---

# Claude Code (built-in)

<v-click>

<div class="mt-8 p-6 bg-neutral-800 rounded-lg max-w-xl">

**Pros:** Works out of the box, no plugins needed

**Cons:** No persistence across sessions, no visualization

</div>

</v-click>

<!--
The built-in TodoWrite tool. Simple, always available, but limited.
-->

---

# Beads

<v-click>

<div class="mt-8 p-6 bg-neutral-800 rounded-lg max-w-xl">

**Pros:** External storage, sync, Claude uses it well

**Cons:** Wild west integration, bring your own review tools

</div>

</v-click>

<!--
Beads gives you external persistence but leaves review up to you.
-->

---

# fp

<v-click>

<div class="mt-8 p-6 bg-neutral-800 rounded-lg max-w-xl">

**Pros:** External storage + integrated review tooling

**Cons:** Smaller community, cloud sync requires account

</div>

</v-click>

<!--
fp is what I use. Disclaimer: I work on it. But I genuinely think the review integration matters.
-->

---

# Other Options

<div class="grid grid-cols-3 gap-4 mt-8">

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Taskmaster**

PRD to tasks

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Vibe Kanban**

Multi-agent, per-task diffs

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg">

**Beans**

Flat-file, token-efficient

</div>

</v-click>

</div>

<v-click>

<div class="mt-8 text-center opacity-70">

*Many more emerging weekly*

</div>

</v-click>

<!--
The space is evolving rapidly. New tools appear all the time.
-->

---
layout: section
---

# Which Should You Use?

<!--
The million dollar question.
-->

---

# Explore What's Out There

<div class="mt-8">

<div class="text-xl opacity-80 mb-8">

There's no "best" tool - find what fits your workflow

</div>

</div>

<div class="grid grid-cols-3 gap-4 mt-6">

<v-click>

<div class="p-4 bg-blue-500/10 rounded-lg">

<div class="text-lg font-semibold mb-2">Try a few</div>

Each has different strengths

</div>

</v-click>

<v-click>

<div class="p-4 bg-green-500/10 rounded-lg">

<div class="text-lg font-semibold mb-2">Match your style</div>

CLI-first? Visual? PRD-driven?

</div>

</v-click>

<v-click>

<div class="p-4 bg-purple-500/10 rounded-lg">

<div class="text-lg font-semibold mb-2">Iterate</div>

Switch if something isn't working

</div>

</v-click>

</div>

<v-click>

<div class="mt-8 text-center opacity-70">

The important thing is having *some* structure for your agent's memory

</div>

</v-click>

<!--
My honest advice: try a few and see what clicks.
The space is young and evolving fast.
-->

---
layout: center
---

<div class="text-center">

# Thank You

<div class="mt-6 text-lg">

**Brett Beutell** · Engineering Lead @ Fiberplane · Amsterdam

</div>

<div class="flex justify-center gap-6 mt-6 text-sm">

<a href="https://twitter.com/lastgoodhandle" target="_blank" class="flex items-center gap-2 text-blue-400 hover:text-blue-300 no-underline">
<span>𝕏</span> @lastgoodhandle
</a>

<a href="https://github.com/brettimus" target="_blank" class="flex items-center gap-2 text-blue-400 hover:text-blue-300 no-underline">
<mdi-github /> @brettimus
</a>

<a href="https://linkedin.com/in/brettbeutell" target="_blank" class="flex items-center gap-2 text-blue-400 hover:text-blue-300 no-underline">
<span>in</span> brettbeutell
</a>

</div>

<v-click>

<div class="mt-10 px-6 py-4 bg-neutral-800 rounded-lg inline-block text-sm">

<div class="flex items-center justify-center gap-2 mb-3">
<span>🤖</span>
<span>Built by Claude Code, tracked with</span>
<img src="/fiberplane-logo.svg" class="w-4 h-4 inline fp-logo-white" alt="fp" />
<span>fp</span>
</div>

<a href="https://github.com/brettimus/cc-task-managers-talk" target="_blank" class="flex items-center justify-center gap-2 text-blue-400 hover:text-blue-300 no-underline">
<mdi-github class="text-base" /> View the code
</a>

</div>

</v-click>

</div>

<!--
Thank you! This talk was built by Claude Code using fp.
Happy to chat about agent workflows, task managers, or how this was made.
-->
