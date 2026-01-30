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

# Task Managers for Claude Code

From chaos to clarity in agent workflows

<div class="abs-br m-6 text-sm opacity-60">
Brett Beutell · @bbeutell
</div>

<!--
Welcome everyone! Today I want to show you something a bit different...
-->

---

# This Talk Is a Demo

Every slide you're seeing was tracked as a task

```
CCTA-vojsagkz [in-progress] Slide content: Meta demo opening
CCTA-dtwfhyzi [todo] Deploy Slidev deck as Cloudflare Worker
CCTA-fesnsfxb [todo] Create private GitHub repo and push initial code
CCTA-fogpceik [todo] Slide content: Plan → Execute → Review framework
CCTA-gyivmtgb [todo] Slide content: Closing and resources
CCTA-mspiiwwi [todo] Slide content: Pain points of agent work
CCTA-pqcfzgfs [todo] Slide content: The landscape of agent-native task managers
CCTA-bulmdiry [done] Initialize Slidev presentation with Bun
CCTA-gszknhfx [done] Set up Poke notification script for slide progress
```

<v-click>

**A Claude Code agent built this presentation, tracking its own work with `fp`**

</v-click>

<!--
This is actual output from fp tree, right now.
I'm not just talking about task managers - I'm using one to build this talk.
-->

---

# The Agent Workflow

<div class="grid grid-cols-3 gap-8 mt-8">

<div class="text-center">
<div class="text-4xl mb-2">📋</div>

### 1. Claim

```bash
fp issue update \
  --status in-progress \
  CCTA-vojsagkz
```

</div>

<div class="text-center">
<div class="text-4xl mb-2">⚡</div>

### 2. Work

```bash
# Make changes
git commit -m "feat: ..."

# Log progress
fp comment CCTA-vojsagkz \
  "Added slides..."
```

</div>

<div class="text-center">
<div class="text-4xl mb-2">✅</div>

### 3. Complete

```bash
fp issue update \
  --status done \
  CCTA-vojsagkz
```

</div>

</div>

<v-click>

<div class="mt-8 text-center text-lg opacity-80">

Every commit links to an issue. Every session has context.

</div>

</v-click>

<!--
This is the basic pattern. Claim work, do work, mark done.
The magic is that this state persists across sessions and context windows.
-->

---

## The Problem

AI coding agents struggle with:

- **Context loss** between sessions
- **No persistent memory** of work in progress
- **Scattered commits** with unclear purpose
- **Lost progress** when context windows reset

---

## The Solution

Agent-native task managers that:

- Track work across sessions
- Link commits to issues
- Log progress at milestones
- Provide clear handoff context

---

## Demo: Live Agent Workflow

*This presentation was built by a Claude Code agent using an agent-native task manager*

- Watch the issue tracker in real-time
- See how progress is logged
- Observe the Plan → Execute → Review cycle

---

## The Landscape

Current tools for agent task management:

- **fp** - Fiber's issue tracking CLI
- **Taskmaster** - AI-native task orchestration
- **Built-in TodoWrite** - Claude Code's native tool

---

## Plan → Execute → Review

The agent workflow pattern:

1. **Plan**: Claim an issue, understand requirements
2. **Execute**: Implement with frequent commits
3. **Review**: Self-review + automated checks
4. **Complete**: Mark done, log handoff notes

---

## Key Takeaways

- Agents need persistent task context
- Progress logging enables session continuity
- Commit discipline links code to purpose
- Review automation catches issues early

---

## Resources

- **fp CLI**: Task tracking for AI agents
- **Claude Code**: Anthropic's coding agent
- **This deck**: Built with Slidev + Bun

---

## Thank You

Questions?

*This presentation is a meta-demonstration of the concepts it presents.*
