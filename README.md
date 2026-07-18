---
name: Solomon PRM Starter Kit
one_liner: A personal relationship manager — remember who you love, stay in touch, and see what actually resonates.
screenshots: []
# 0.2.4 = the first app build whose .base importer maps Obsidian `or:`
# filter groups to OR base-DSL (Inner Circle.base is wrong — shows ALL
# people, with a warning — on anything older).
min_app_version: 0.2.4
---

# Solomon PRM Starter Kit

A **personal relationship manager (PRM)**: a small, opinionated vault for
keeping up with the people you care about — offline. This kit answers three
questions:

1. **Who am I overdue to contact?** (`Bases/Overdue.base`, the check-in
   queue widget on the front door, and the Monday `prm-checkin` agent.)
2. **What do the people I love actually care about?** (each person's `##
   They care about` / `## Likes & gifts` / `## Open threads` sections.)
3. **What engagements resonate?** (per-interaction `resonance` scores,
   aggregated monthly by the `prm-resonance` agent into `## What resonates`.)

## Get started

Open `PRM/Start Here.md` — it's the front door and walks you through logging
your first real interaction. Three fictional people (Ada, Marcus, Priya) and
six interactions ship as seed content so every base and the check-in widget
render non-empty the moment you open this vault; delete `People/` and
`Interactions/` content once you've read through it and replace it with your
own.

## What's inside

- **`People/`** — one note per person (`Templates/Person.md`).
- **`Interactions/`** — one note per touch: call, meal, text, gift, letter
  (`Templates/Interaction.md`).
- **`PRM/`** — `Start Here.md` (front door), `Check-in Queue.md`
  (agent-maintained, Monday mornings), `Weekly Review.md` (your ritual).
- **`Bases/`** — five saved queries: `People`, `Overdue`, `Inner Circle`,
  `Recent Interactions`, `High Resonance`. Authored as Obsidian Bases YAML,
  so the same files open natively under Obsidian's Bases plugin;
  `Inner Circle.base` uses a native `or:` filter group, which Solomon
  imports as one OR where-line (`where circle is "family" or circle is
  "close"`) and exports back to the identical `or:` group — lossless both
  ways. See "Honest limitations" for how these load in Solomon today.
- **`Widgets/checkin-queue.html`** — a live table of who's overdue, embedded
  in `PRM/Start Here.md`.
- **`Skills/prm/SKILL.md`** — the operating playbook (add a person, log an
  interaction in under a minute, run the weekly review).
- **`Agents/`** — `prm-welcome` (greets a new person note), `prm-checkin`
  (Monday 8am: proposes the check-in queue), `prm-resonance` (monthly:
  proposes `## What resonates` updates). All three are **propose-by-default**
  (`auto_accept: false`, `tier: editor`) — they never write to your vault
  without your review.

## Two-field schema, on purpose

This kit deliberately has exactly two content types — `person` and
`interaction` — not the ~20 entity types a full CRM has. Every field you add
to `Templates/Person.md` is friction the next time you log someone; the
skill's "under 60 seconds" bar is the design gate. If a field goes unfilled
for a few weeks, cut it.

## Honest limitations (read before you rely on this)

- **`.base` files are import-only in Solomon today — they don't
  auto-appear.** Solomon's Bases surface shows its own saved bases, not the
  vault's `.base` files; nothing in `Bases/` renders anywhere until you load
  it. To use one: open the Bases surface → the **⇅ .base** button →
  **Import** tab → pick the file from the vault list (or paste its YAML).
  Importing
  loads the query into the DSL editor of the *active* base — it replaces
  that base's current query, so add a new base first if you want to keep
  what's there. One file at a time; there's no "import the whole folder as
  five saved bases" yet. The `.base` files stay the portable source of
  truth: the queries themselves (including `Inner Circle.base`'s OR group
  and `Overdue.base`'s relative `now-30d` window) survive the import
  losslessly on app 0.2.4+.
- **Overdue detection uses a coarse 30-day window** (`last_contact lt
  now-30d`) — real per-person cadence (`cadence_days`) is handled
  agent-side by `prm-checkin`, not by the base query itself (the base DSL
  can't compare one field against another yet). The 30-day default, and
  whether cadence should vary by circle (family 14 / close 30 / friend 90),
  are open calls — live with the default a week before you decide it's
  wrong.
- **Cron agents only fire while the desktop app is open.** If you don't open
  Solomon on a given Monday, that week's check-in queue silently doesn't
  regenerate. There's no server-side scheduling yet.
- **This is local-only by default** (no `.solomon/`, see `.gitignore`
  above). PRM data — who you love, what they're going through — is about as
  sensitive as vault content gets; read what enabling sync means (it puts
  plaintext on Solomon's sync plane) before you turn it on.
- **The `circle: family|close|friend|professional` taxonomy is a guess.**
  Live with it before it freezes into muscle memory.
- This kit's permanent home (a dedicated repo, org, and license) is still an
  open founder decision — for now it lives at `kits/solomon-kit-prm/` in the
  main Solomon repo. The content here is directory-portable: copying this
  folder out as its own git repo (with its own `git init`) is exactly how it
  will eventually ship.
