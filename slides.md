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
layout: section
---

# The Pain

Why agents struggle without structured memory

<!--
Let's talk about what's broken. Because if you've used Claude Code for any serious project, you've felt these problems.
-->

---

# The "50 First Dates" Problem

<div class="text-xl mt-8 opacity-80 italic">
"Every morning, your AI wakes up with no memory of yesterday."
</div>

<div class="text-sm mt-2 opacity-60">— Steve Yegge</div>

<v-clicks>

<div class="mt-8">

- **New context window** = clean slate
- Yesterday's progress? Gone.
- That brilliant plan you worked out together? Forgotten.
- Your coding style preferences? Explain them again.

</div>

<div class="mt-6 p-4 bg-orange-500/10 rounded-lg">

**The irony:** The agent was doing great work. You were making progress. Then the session ended.

</div>

</v-clicks>

<!--
Steve Yegge coined this analogy - like the movie 50 First Dates where Drew Barrymore's character has no memory of previous days.
Every session starts from scratch.
-->

---

# Your Brain Lives Elsewhere

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

### Where the plan lives

- Your head
- Notion / Linear / Jira
- Random Slack messages
- That email you sent yourself

</div>

<div>

### Where Claude works

- The current context window
- *(that's it)*

</div>

</div>

<v-click>

<div class="mt-8 p-4 bg-red-500/10 rounded-lg text-center">

**Gap:** You constantly re-explain the big picture

"Remember we're building a billing system..."

"The goal is to migrate users to the new API..."

</div>

</v-click>

<!--
This is the fundamental disconnect. You have all this context about what you're building, why, what's next.
But every session you need to reload that into the agent.
-->

---

# Context Rot

<div class="mt-8">

Session 1: "Let's build the authentication system"

<v-clicks>

Session 5: "Wait, what approach did we decide on for refresh tokens?"

Session 10: "Did we handle the edge case where..."

Session 20: "I think we need to refactor this, but I'm not sure what the original design was"

</v-clicks>

</div>

<v-click>

<div class="mt-8 p-4 bg-yellow-500/10 rounded-lg">

**Each session starts slightly out of sync.** Context doesn't just disappear — it degrades over time.

</div>

</v-click>

<!--
Even when you try to maintain continuity, information degrades.
You remember differently than the agent remembers.
Neither of you remember exactly what was decided.
-->

---

# Markdown Litter

<div class="mt-8 font-mono text-sm bg-neutral-800 p-4 rounded-lg">

```
project/
├── TODO.md          (last updated 3 weeks ago)
├── PLAN.md          (from that one session)
├── NOTES.md         (who wrote this?)
├── ARCHITECTURE.md  (is this current?)
├── .claude/
│   └── TODO.md      (wait, there's another one?)
└── docs/
    └── ROADMAP.md   (definitely stale)
```

</div>

<v-clicks>

<div class="mt-6">

- Agents create markdown files to "remember"
- These files go stale almost immediately
- You don't want to commit them
- But you need *something* for context

</div>

<div class="mt-4 text-lg opacity-80">

**Result:** A graveyard of good intentions

</div>

</v-clicks>

<!--
Every agent session leaves behind markdown artifacts.
The agent is trying to help! But without a real system, these files just become noise.
-->

---

# The PR Review Problem

<div class="grid grid-cols-2 gap-8 mt-8">

<div>

### Agent makes 47 commits

```
feat: add user model
feat: add validation
fix: validation edge case
refactor: extract helper
feat: add tests
fix: test was wrong
...
```

</div>

<div v-click>

### You need to review

- What was the plan?
- Why these decisions?
- Did anything get missed?
- Is this even right?

</div>

</div>

<v-click>

<div class="mt-8 p-4 bg-purple-500/10 rounded-lg">

**The trust problem:** You can't verify work you can't understand.

And you can't understand work without context.

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
