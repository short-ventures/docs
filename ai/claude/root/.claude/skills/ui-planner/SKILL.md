---
name: plan-ui
description: Use before UI work to understand preferences and patterns
---

When creating UI, your first goal should be to locate a similar pattern that we can copy or gain understanding from:
1. Explore the `/front` folder to find references and similar UI concepts
2. See which generic components can be applied or extended
3. Understand which colours we use

## Components
- We love to use shadcn components for inspiration
- Always look for similar components that can be extended or used, to prevent duplicate component overlap
- When changing components directly, ensure there is no collateral impacts
- Explore existing components for colour and design patterns

## Optimistic UI
Where possible, we like to use optimistic UI patterns.
You will need to make a decision as to whether it is appropriate:

1. If the API request creates a response with information that needs to then be displayed in the UI, optimistic patterns are not a good fit.
2. If the API is making a simple CRUD request that does not need to await for a response payload, optimistic UI patterns should be used.

If you're ever unsure - you should ask the user.