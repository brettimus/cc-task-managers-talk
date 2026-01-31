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

# What Would Claude Build?

<div class="text-center mt-12">

<div class="text-xl opacity-80 leading-relaxed max-w-2xl mx-auto">

If you ask Claude to build a tool for itself to be more effective,

you will end up with a **task manager**.

</div>

</div>

<v-click>

<div class="mt-12 text-center opacity-60">

Let's find out why.

</div>

</v-click>

<!--
What would Claude build for itself? Task management. Every time.
It's not a coincidence - it's a necessity.
-->

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
<mdi-github class="text-lg" />
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
I'm Brett, I work at Fiberplane. We built fp, the task manager I'll be showing you today.
-->

---

# Meta Demo

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

# Pain Point 1

Ambitious work requires multiple Claude Code sessions

<!--
Let's start with the first problem you'll hit when doing real work with Claude Code.
-->

---

# Why Multiple Sessions?

<div class="grid grid-cols-3 gap-4 mt-6">

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg text-center">

**Context is finite**

Performance degrades as you add more

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg text-center">

**Compaction isn't great**

Getting better, but lossy

</div>

</v-click>

<v-click>

<div class="p-4 bg-neutral-800 rounded-lg text-center">

**Wrong turns happen**

Dead ends deserve documentation

</div>

</v-click>

</div>

<v-click>

<div class="mt-8 p-4 bg-orange-500/10 rounded-lg text-center">

**Any ambitious project spans multiple sessions**

</div>

</v-click>

<!--
Context windows are finite. Eventually you need to start fresh.
But how do you carry forward what you learned?
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

<div class="p-4 bg-red-500/10 rounded-lg">

### Codebase clutter

- SPEC.md, PLAN.md, TODO.md, DEV_LOG.md
- Which one is current?
- Do you commit them?

</div>

</v-click>

<v-click>

<div class="p-4 bg-red-500/10 rounded-lg">

### Lost explorations

- Failed approaches don't survive squash
- "Why didn't we do X?" - no record
- Reasoning evaporates

</div>

</v-click>

</div>

<v-click>

<div class="mt-6 p-4 bg-yellow-500/10 rounded-lg text-center">

**We need structured persistence, not scattered docs**

</div>

</v-click>

<!--
The core problem: these ad-hoc solutions don't scale.
They clutter your repo and still lose information.
-->
