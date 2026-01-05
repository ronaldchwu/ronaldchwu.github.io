---
title: "First Personal Productivity Experiment"
date: 2026-01-05
categories: 
  - AI Engineering
tags:
  - Writing
  - Productivity
classes: wide
toc: true
toc_label: "Table of Contents"
toc_icon: "cog"
---

Lately, I've been experimenting with AI tools as collaborators to solve everyday pain points.  Not just for coding, but for product thinking and personal productivity routines.  This post is a short reflection on a small example:  using AI agents to prototype a personal Product Management workspace, with credit card statement analyzer as my first POC (yes, reviewing statement transactions records is a recurring pain).

The PM Workspace lived as a git repo folder. The real goal wasn't the code. It was to see:  How quickly & easily can I define a problem, scope it down, and get something genuinely useful from today's AI agents?

### The Setup:  A Multi-Tool Workflow

I started with a fairly opinionated setup.

On the left screen, I used Google Antigravity as 'VSCode plus a clear, interactive implementation plan'.  It excelled at breaking down complex/ambiguous tasks, walking through the steps, and addressing my comments before executing.  On the right screen, I paried ChatGPT / Gemini / Claude Chat (chrome) with Claude Code / Codex CLI (terminal). This is where I brainstorm ideas with chatbot and delegate well-defined tasks to agent.  On a third screen,  I used Typora to co-edit Markdown files (PRD.md, user-stories.md) in near realtime. I could see AI agents evolve the files and address my in-line comments.    

This turned out to be a fairly nice workflow experience:  

- I have chatbots turning discussion threads into draft product idea ('Credit Card Analyzer')
- Claude Code drafts PRD.md and user-stories.md in a 'credit-card-analyzer' sub-folder
- Iteratively, I review the .md files in Typora (comments marked as TODOs), then collaborate with Antigravity's Gemini agent to refine them (tweak and approve its Implementation Plan).
- Once happy with PRD/user-story, Claude Code implements the POC codebase. 
- I test the POC pipeline, and work with either Claude Code, Codex CLI or Antigravity to fix bugs or modify feature scope/design.

### Tool Level Observation

A few patterns emerged pretty quickly.

Claude was the most fluent overall. It understood intent well, used web search effectively, and communicated progress clearly.  I can easily add real-time feedback/pivoting command as well.   But even Opus 4.5 once mis-implement a core part of my desired flow --- it hallucinated a `corrections.json` file that was never part of the spec. My guess is that it was layering “best-practice design” on top of a deliberately simple user story.

Antigravity's interactive Implemetation Plan and Multi-agent management offer reliable user experience ----- I felt in control of what's being done. It was consistent when using Gemini 3.0 Flash, yet Gemini 3.0 Pro sometimes jumped straight into editing codes/files.     

In reviewing POC codebase, Gemini 3.0 Flash in Antigravity only surfaced superficial issues, while Codex CLI caught several UI/UX flow inconsistency. 

Codex CLI had a different set of problems. It often couldn’t figure out what tools or packages were available, and it got stuck more than I expected. It also tended to overreach. For example, when I moved from PRD v1.1 to v1.2—only a few minor changes—Codex suggested a much broader set of improvements. In comparison, Antigravity’s implementation plan stayed closer to the actual delta.



### About using the Credit Card Analyzer

After two mornings of work, I started using **credit card analyzer v1.4** on two NAB statements.

The results were encouraging:

- About 70% of transactions were correctly populated.
- This alone saved a significant amount of copy-pasting.
- More importantly, the AI’s reasoning reduced my mental load. It helped me recall item details smoothly, which made the task feel lighter.

Objectively, the total processing time only dropped by around 15%. Subjectively, though, the experience was much more relaxed. Knowing that my effort—combined with explicit reasoning feedback—could deterministically improve future runs was surprisingly motivating.

There are real downsides. Latency is bad (2–3 minutes per run), token usage is wasteful, and the system currently dumps entire CSVs into context. Still, the total cost was under $0.50, which feels acceptable at this stage. The real question isn’t cost—it’s whether this genuinely increases productivity and value, rather than just *feeling* good.



### Lessons Learned

The biggest early mistake was **scope**. My initial PRD was far too ambitious. By v1.1 and v1.2, I realized I didn’t need any interactive UI at all. LLMs have a strong tendency to over-design and over-plan, so steering them toward a truly minimal POC requires constant discipline.

A few other lessons stood out:

- LLMs still read *too much* in codebase for every new task step. Token usage is inefficient.  
- The manual workflow is fragile. When one agent raises concerns that conflict with another agent’s design logic, reconciliation is hard. The resulting codebase can feel like multiple ICs committing to the same repo without alignment.
  - In practice, it may be better to have *one* agent focused end-to-end: PRD, coding, and review.
- Prompting is still expensive. Without `/commands` or reusable skills, a lot of effort goes into restating context.

### Closing Thoughts

This feels like a good starting point for automating small life errands with AI.  The tools are powerful, but they need careful constraint: smaller scopes, clearer specs, tests from day one, and fewer agents stepping on each other’s toes.   But even in this rough state, it's exciting to see how quickly we can solve everyday problems with AI-assisted workflows.  Can't wait to see how the next experiments can further improve the process.

