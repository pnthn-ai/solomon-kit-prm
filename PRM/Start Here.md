---
type: dashboard
---

# Start Here

Welcome to your PRM. Three fictional people (Ada, Marcus, Priya) and six
interactions are already logged so every base and the widget below render
non-empty — read through them, then replace them with your own.

## Who's overdue

```solomon-widget {"id":"checkin-queue"}
from notes
where type is person
where last_contact lt now-30d
sort last_contact asc
columns circle, last_contact, cadence_days
```

## Your first move

1. Read `Skills/prm/SKILL.md` — it's the whole playbook, two minutes.
2. Pick one real person. Insert `Templates/Person.md`, rename it to their
   name, drop it in `People/`. Write one fact in `## They care about`.
3. Log your last real interaction with them: insert `Templates/
   Interaction.md` into `Interactions/`, fill the four fields
   (`person`/`mode`/`initiated_by`/`resonance`), one line on what happened.
4. Delete the seed content (`People/Ada Okafor.md`,
   `People/Marcus Webb.md`, `People/Priya Sharma.md`, and their matching
   `Interactions/*.md` files) once you've got a feel for the shape.
5. When you're ready for the weekly ritual, open `PRM/Weekly Review.md`.

## The five bases

- `Bases/People.base` — everyone, oldest `last_contact` first.
- `Bases/Overdue.base` — the same query the widget above runs, saved.
- `Bases/Inner Circle.base` — family + close only.
- `Bases/Recent Interactions.base` — your last 20 touches.
- `Bases/High Resonance.base` — the engagements that landed (resonance ≥ 4).
