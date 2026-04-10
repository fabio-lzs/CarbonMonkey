# Global rules

- Respect the existing architecture and conventions in the repository.
- Prefer small, reversible, easy-to-review changes.
- Do not create unnecessary bureaucracy.
- Do not invent run infrastructure, control files, or helper directories unless explicitly requested.
- When a task requires delegation, send each subagent only the minimum context it needs.
- If a request is clear, execute. If it is critically ambiguous, ask a few objective questions.
- Do not use temporary paths outside the workspace.
- Do not read the entire project unless it is actually necessary.
- For async, stateful, event-driven, or external-dependency changes, explicitly think about:
  - completion
  - cleanup
  - loading/busy exit paths
  - ownership of state transitions
  - timeout/no-response behavior
  - cancellation when applicable
  - unmount/remount safety when applicable
  - duplicate trigger and stale-result risks when applicable
- Do not consider a change complete if the UI or system can get stuck in loading, hidden, disabled, busy, syncing, or inconsistent state.
- Do not consider a change safe if listeners, subscriptions, timers, or observers can outlive their intended lifecycle without cleanup.
- Always reply in the same language as the user's latest message.
- Do not mix languages in headings, labels, bullets, summaries, or handoff messages.

- When investigating bugs, explicitly distinguish symptom, trigger, broken transition/lifecycle step, and likely root cause.
- When planning work, include preventive guardrails for plausible failure modes instead of planning only the happy path.
