---
title: "First Personal Productivity Experiment"
date: 2026-01-06
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

## Raw Notes

*Quick capture zone — type thoughts and work notes here as they come. Refactor into proper sections below later.*

---

- Testing Claude Code to create a personal PM workspace (`/Users/ronaldwu/Projects/Q1CY26/playground/02-pm-workspace/`).
- Goal: see how quickly I can define and resolve a personal productivity problem, using credit card statement analysis as the example.
- How I used the AI tools together
  - Antigravity on the left screen as “VSCode with a clear implementation plan + walkthrough + multi‑agent task management.”
  - Claude Chat + Claude Code on the right: most natural and smooth workflow, with great user interaction/collaboration.
  - Typora: updating + co‑editing `.md` files in near realtime (TODO: xxxxxx).
- Antigravity: handy implementation plan and walkthrough, but only with Flash. 3.0 Pro will directly edit `.md` files.
- Claude: super fluent; uses the web search tool effectively; understands intent and shows progress clearly.
  - 3.0 Flash’s review of the POC codebase only found superficial issues, whereas Codex CLI found a few UI/UX flow inconsistencies vs. user stories.
  - Even Opus mis‑implemented my desired user story (hallucinated a `corrections.json` that isn’t part of the story).
    - Maybe Opus was doing best‑practice detailed design on top of my user story.
- Codex CLI:
  - Can’t figure out what tools/packages are available; gets stuck often.
  - Tends to overdo and lose focus on key changes (e.g., PRD v1.1 → v1.2 only had a few minor changes, but Codex suggested other improvements). Antigravity’s implementation plan is more useful.
- Overall observations & learnings
  - Good first step of agent‑human collaboration.
  - PRD: initial scope was too huge. I soon realized that from v1.1/v1.2 onward, no interactive UI/UX is needed. LLMs tend to over‑design and over‑plan. Need careful steering for a minimal POC/MVP.
  - LLMs still read too many lines; token usage is not efficient.
  - Technically: it’s easy to send a PDF into chat and get results, but the real value is leveraging historical data with robust, consistent data I/O checks.
  - Current manual workflow is not smooth.
    - When one AI agent raises concerns, it’s hard to reconcile with another agent’s design logic/justification. The resulting codebase can become a hybrid and unstable thing—like multiple ICs working on the same repo.
      - Maybe it’s better to have one agent totally focused on PRD, coding, reviewing, etc.
    - The lack of `/command` or skill makes prompting time‑consuming and redundant.
    - Starting with NO tests is a mistake—none of the AI agents proactively started even a simple E2E test. Need to add this to `CLAUDE.md` or `AGENTS.md`.
  - Day 2 (Jan 4, 2026): I got an initial output CSV quickly, but soon ran into bugs and the pipeline stopped working. Debugging became difficult because I hadn’t set up tests properly.
- Credit card analyzer v1.4 POC
  - I started using it on my two NAB statements on Jan 5, 2026
    - Successfully populated 70% of transactions. Saved a lot of copy pasting speeds.
    - AI Reasoning really help reduce my mental load! It helps me recall the item details smoothly

  - Although my overall time in processing the statements are only reduced by 15%, I feel much more relaxed in doing the task.
    - Plus, knowing that the efforts I put in (+ User Reasoning) can help future improvement deterministically is very motivating.

  - I see this is a good start of AI-automating my life errands. 
    - Latency and token usage are terrible (2-3min;  dumpped all CSV files).  But total costs are <$0.5 and seem good enough. Nevertheless, I should be cautious that it is really make me more productive and generating values, not just 'feeling good'.
    - Improving latency and token usage are still must-do in long term. 



---

## Refined Content

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

