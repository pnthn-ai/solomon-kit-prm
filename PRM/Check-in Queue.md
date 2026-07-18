---
type: dashboard
---

# Check-in Queue

Rewritten every Monday morning by the `prm-checkin` agent (see
`Agents/prm-checkin.md`) — a ranked list of who you're overdue to contact,
each with one concrete suggested engagement. Every rewrite lands as a
proposal in your Review queue; nothing here changes without you accepting
it.

**This only fires while the desktop app is open on a Monday.** If a week
goes by without the app open, that week's queue just doesn't refresh — check
`_last_run` below (once the agent has run at least once) if the list looks
stale.

_No run yet — open the desktop app on a Monday, or trigger the agent
manually, to generate the first queue. Until then, `Bases/Overdue.base`
(and the widget on `PRM/Start Here.md`) is always live and current._
