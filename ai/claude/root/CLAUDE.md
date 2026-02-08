# Instruction
- Proactively use the skills that are available
- Don't run servers, the user does this for you
- You can run other commands such as migrations, linters
- Always aim to clean up redundant/inefficient code
- Ask questions proactively if you require clarity
- Always start by finding code patterns that you can copy
- Don't create .MD files unless requested

# Repository overview
This repo is a multi-project workspace for Blox with four main parts:

- `back/`: Rails 8 API application for the core Blox back-end (PostgreSQL + Redis/Sidekiq).
- `front/`: TanStack Start + React front-end UI, built with Vite and Tailwind.
- `ruby_llm/`: Ruby gem providing a unified LLM client API (vendored here and used by the back-end).
- `blox_pages/`: The Cloudflare Worker for deploying and hosting Blox landing pages

## Back
- Keep APIs consistent with each other and predictable
- Ensure you use authentication and authorization logic already applied
- Use Sidekiq for background jobs and services to encapculate logic
- We use `Rails.application.credentials`, not `ENV.fetch`

## Front
- Use `pnpm`
- Use eslint after each feature implementation
- Use shadcn as a component library
- Use phosphor for icons
- Always ensure you're not creating duplicate component files
- Always use optimistic UI patterns when consuming APIs

# Execution

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.