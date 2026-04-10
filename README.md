# CarbonMonkey Factory a Copilot Multi-Agent Team 

Goal:
- keep specialized squads
- keep visible orchestration
- remove bureaucracy
- avoid unnecessary nested subagents
- use the Router only as a classifier and prompt improver
- make the internal system globally portable
- catch more async, lifecycle, cleanup, and concurrency bugs before they ship

## Quick start
1. Copy the `.github/` folder from this repository into the root of your project.
2. Open the project folder in VS Code.
3. Enable this setting in `settings.json`:

```json
"chat.customAgentInSubagent.enabled": true
```

4. Run **Developer: Reload Window**.
5. Open a new Copilot chat.
6. Choose a squad directly for normal work, or use `/work` when you want routing help plus a rewritten prompt.

## How to use
### Direct squad workflow (recommended)
Pick the squad that matches the job and talk to it directly.

Examples:

```text
Bug Squad
After implementing Firebase login, the screen stays gray after sign-in and there are no console errors. Find the root cause and fix it.
```

```text
Feature Squad
Add list sharing so the owner can invite other users by email and choose whether they can edit or only view.
```

```text
Project Squad
Create a new MVP from scratch for a collaborative shopping list with Firebase, Google login, and PWA support.
```

### Router workflow (optional)
Use `/work` only when you are not sure which squad should handle the request.

Example:

```text
/work
I want to improve this flow but I am not sure whether this is a bug, a refactor, or a feature.
```

Expected result:
- request classification
- recommended squad
- improved prompt ready to paste into that squad

### Choosing the right squad
- **Bug Squad**: bugs, regressions, broken behavior, root-cause analysis
- **Feature Squad**: new functionality in an existing project
- **Project Squad**: greenfield, bootstrap, new MVP, project from scratch
- **Refactor Squad**: structural cleanup without intended behavior change
- **Performance Squad**: slowness, bottlenecks, render/query/runtime performance
- **Integration Squad**: APIs, auth providers, webhooks, SDKs, external services
- **Docs Squad**: README, onboarding, technical documentation, usage guides

## Recommended usage
- **Default:** select the squad directly
- **When unsure:** use `/work` or select `Router Squad`

## How to operate
### Recommended mode
1. You choose the right squad and talk to it directly.
2. The squad coordinates the specialists.
3. The specialist analyzes.
4. Builder · Bob implements.
5. Reviewer · Kyle reviews.

### When to use the Router
Use the Router only to:
- classify ambiguous requests
- discover which squad to use
- receive an improved prompt to paste into the right squad

The Router **does not delegate**.

## Squad flows
- Feature Squad: Paul optional -> Art -> Bob -> Kyle
- Project Squad: Paul -> Art -> Bob -> Kyle
- Bug Squad: Ivy -> Bob -> Kyle
- Refactor Squad: Rhea -> Bob -> Kyle
- Performance Squad: Pax -> Bob -> Kyle
- Integration Squad: Iris -> Bob -> Kyle
- Docs Squad: Dora -> Kyle

## Runtime correctness scope
This hardening is not only about Promises. It now applies to:
- promises and awaits
- callbacks
- event listeners
- subscriptions and realtime listeners
- polling, websockets, timers, and intervals
- auth/session listeners
- retries and background sync
- optimistic UI and external-dependency flows

Bob should think about:
- completion
- cleanup
- ownership of state
- duplicate triggers
- stale results
- unmount/remount behavior

Kyle should reject when any of these are unclear:
- completion path
- cleanup path
- loading/busy exit path
- listener/subscription/timer ownership
- plausible race or stale-result handling

## Principles
- no `.ai-workflow`
- no mandatory run infrastructure
- no code reading by the Router
- no code reading by visible squads
- specialists analyze
- Bob implements
- Kyle reviews

## Visual validation
Internal agents have prefixed names so they are easier to spot in the UI:
- Planner · Paul
- Architect · Art
- Builder · Bob
- Reviewer · Kyle
- Bug · Ivy
- Refactor · Rhea
- Performance · Pax
- Integration · Iris
- Docs · Dora

## Language behavior
- Internal prompts and instructions are in English.
- Agents must reply in the same language as the user's latest message.
- If the user writes in English, outputs should be fully in English.
- If the user writes in Portuguese, outputs should be fully in Portuguese.

## Prerequisite
Enable this in VS Code:

```json
"chat.customAgentInSubagent.enabled": true
```

Then:
- run Developer: Reload Window
- open a new chat
- use the direct squad flow by default
- use `/work` only when you want classification plus an improved prompt
