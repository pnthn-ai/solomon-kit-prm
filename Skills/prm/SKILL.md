---
name: PRM
description: How to run this vault as a personal relationship manager — add a person, log an interaction in under a minute, and work the weekly review.
tags: [prm, relationships, workflow]
---

# PRM

This vault has exactly two content types — `person` and `interaction` — plus
three dashboard notes under `PRM/`. This skill is the whole operating
playbook; if you're an agent following it, don't add fields or steps beyond
what's here without being asked.

## The frontmatter contract

Every `Person` note (`People/<Full Name>.md`) carries:

- `type: person` — how bases and agents find it.
- `cadence_days` — how often you want to be in touch (a number; 30 is the
  kit default).
- `last_contact` — ISO date (`YYYY-MM-DD`) of the last real touch. Kept
  current by the `prm-checkin` agent when it sees a new `Interaction` note
  for that person; you can also hand-edit it.
- `overdue` — boolean, agent-stamped. Belt-and-braces alongside
  `Bases/Overdue.base`'s own `last_contact lt now-30d` predicate.
- `birthday`, `circle` (`family`/`close`/`friend`/`professional`), `city`,
  `channels` (list) — static facts, hand-edited.

Every `Interaction` note (`Interactions/<YYYY-MM-DD> <Full Name>.md`)
carries:

- `type: interaction`, `person` (a `[[People/<Full Name>]]` link),
  `date`, `mode` (`in-person`/`call`/`video`/`text`/`gift`/`letter`),
  `initiated_by` (`me`/`them`).
- `resonance` — 1–5, how much the engagement landed. This scores the
  *engagement*, not the person — it's telling you what to do more of, not
  grading your relationships.
- `next_step` — the one thing to follow up on.

## Add a person

1. Insert `Templates/Person.md`, rename it to the person's full name, drop
   it in `People/`.
2. Fill in `circle`, `birthday`, `city` if known — otherwise leave blank.
3. Write **one fact** in `## They care about`. That's the minimum bar; more
   can come later.
4. If sync is on, the `prm-welcome` agent proposes filling in anything you
   left blank — review and accept what's right.

## Log an interaction (under 60 seconds)

1. Insert `Templates/Interaction.md` into `Interactions/`, rename it
   `<YYYY-MM-DD> <Full Name>.md`.
2. Fill `person`, `mode`, `initiated_by`, `resonance` — four fields, that's
   the whole form.
3. One line in the body on what happened. If they mentioned something worth
   remembering, copy it into their `## They care about` or `## Open
   threads` while it's fresh — don't rely on remembering to do it later.
4. Done. `last_step` (`next_step`) can wait for the weekly review if you're
   in a hurry.

If a field is regularly going unfilled, cut it — friction here is a dropout
risk, not a data-quality problem to fix with more fields.

## The weekly review ritual

1. Open `PRM/Weekly Review.md`.
2. Work `Bases/Overdue.base` top to bottom (oldest `last_contact` first) —
   for each person, either reach out now or note *why not* in their `##
   Open threads`.
3. Pick **one** relationship to move offline this week — book the
   in-person thing, not just another text.
4. Skim `PRM/Check-in Queue.md` (the agent's Monday proposal, if you've
   accepted it) and `## What resonates` on a couple of people — let the
   monthly resonance report change *how* you engage, not just how often.

## Logging honestly

`resonance` is for you, not them — nobody sees it but you and the
`prm-resonance` agent. Score the engagement candidly even when it stings a
little; a string of low scores on one channel with one person is exactly
the signal that should change what you do next, and it only works if the
numbers are real.
