# Copilot Three-Agent Team v6.5

v6.5 keeps the v6.4 operating model and additionally hardens Bug · Ivy for root-cause analysis and Architect · Art for prevention-aware planning.

Goal:
- keep specialized squads
- keep visible orchestration
- remove bureaucracy
- avoid unnecessary nested subagents
- use the Router only as a classifier and prompt improver
- make the internal system globally portable
- catch more async, lifecycle, cleanup, and concurrency bugs before they ship

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


## What changed in v6.5
- Bug · Ivy now distinguishes symptom, trigger, broken transition/lifecycle step, and likely root cause.
- Ivy now ranks alternative plausible causes and reports evidence plus confidence instead of stopping at the first suspicious area.
- Architect · Art now plans with failure prevention in mind, not only happy-path delivery.
- Art now explicitly includes guardrails for async, lifecycle, cleanup, ownership, timeout, and stale-result risks when relevant.
- This reduces the chance of Bob implementing a plan that is technically coherent but fragile in runtime behavior.

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
