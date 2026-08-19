---
type: dashboard
---

# Start Here

Open this folder as a vault in Solomon (desktop, Mac Apple Silicon, 0.2.4 or newer; 0.3.0 is current). The table below should be a live check-in queue, not a code fence. Three fictional people are already logged so it is not empty.

## Who's overdue

```solomon-widget {"id":"checkin-queue"}
from notes
where type is person
where last_contact lt now-30d
sort last_contact asc
columns circle, last_contact, cadence_days
```

If the queue is a fenced code block, stop. That means Solomon is not running this vault. Install the signed app (Mac, Apple Silicon only): https://app.lomon.dev/api/desktop/update/download?tag=v0.3.0&asset=Solomon_0.3.0_aarch64.dmg then open this folder as a vault.

## Your first move

1. Pick one real person. Insert `Templates/Person.md`, rename it to their name, drop it in `People/`. Write one fact in `## They care about`.
2. Log your last real interaction with them: insert `Templates/Interaction.md` into `Interactions/`, fill `person` / `mode` / `initiated_by` / `resonance`, one line on what happened.

That is first-run. You are done when one real person and one real interaction exist.

When you are ready, delete the seed people (`People/Ada Okafor.md`, `People/Marcus Webb.md`, `People/Priya Sharma.md`) and their matching `Interactions/*.md` files. The operating playbook is `Skills/prm/SKILL.md`. Weekly ritual is `PRM/Weekly Review.md`.

## Bases (import-only)

`.base` files in `Bases/` do **not** auto-appear in Solomon. They are the portable source of truth. To use one: Bases surface → **⇅ .base** → **Import** → pick the file. Importing replaces the active base's query, so add a new base first if you want to keep what is there. One file at a time.

- `Bases/People.base` — everyone, oldest `last_contact` first.
- `Bases/Overdue.base` — the same query as the widget above.
- `Bases/Inner Circle.base` — family + close only.
- `Bases/Recent Interactions.base` — last 20 touches.
- `Bases/High Resonance.base` — resonance ≥ 4.
