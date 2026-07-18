---
type: dashboard
---

# Weekly Review

A 5-minute ritual, once a week. Full steps in `Skills/prm/SKILL.md`; short
version:

1. **Work the queue.** Open `Bases/Overdue.base` (or `PRM/Check-in Queue.md`
   if the Monday agent has run) top to bottom. For each person: reach out
   now, or write down *why not* in their `## Open threads`.
2. **Move one relationship offline.** Pick one person and book the
   in-person thing — a call, a meal, a visit. Not another text.
3. **Skim what's resonating.** Glance at `PRM/Resonance Report.md` and a
   couple of people's `## What resonates` sections. Let it change *how* you
   engage this week, not just how often.
4. **Log as you go.** Every real interaction this week gets an
   `Interactions/` note — under 60 seconds each, per the skill.

```solomon-widget {"id":"checkin-queue"}
from notes
where type is person
where last_contact lt now-30d
sort last_contact asc
columns circle, last_contact, cadence_days
```
