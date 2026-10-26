# STATUS — Hospital Stay Companion Guide

As of 2026-10-26.

## What was built

A complete, education-only, never-medical-advice manual for planned and
surprise hospital stays, in the house style of the sibling guides
(plain English, warm, step by step):

- `docs/index.md` — Start Here: two paths (planned vs. surprise stay),
  who it's for, the whole guide in eight sentences, and the guide's two
  standing rules (translate paperwork, never interpret it; handle
  logistics, never medicine).
- `docs/01-packing.md` — what to pack and what to leave home; core
  list, planned-stay pre-packing evening, and the surprise-stay scout
  list.
- `docs/02-admission-paperwork.md` — the usual admission folder
  translated to plain words (consent to treat, procedure consent,
  financial agreement, privacy/HIPAA paperwork, contact and
  advance-directive forms), the four questions worth asking at the
  admitting desk, and interpreter/help requests.
- `docs/03-bedside-helper.md` — the journalist-and-butler role: note
  habits, mid-stay intel to collect, the hard stops (never diagnose,
  never negotiate at the bedside, never post privately-gathered
  photos), and a note about the helper's own welfare.
- `docs/04-teach-back.md` — the teach-back habit: the universal
  opener, four playbacks at admission, the seven playbacks at
  discharge, and how to use it when the patient is the one learning.
- `docs/05-discharge-checklist.md` — the discharge folder decoded in
  five parts: the med list (new/changed/stopped/unchanged), follow-ups
  (who books whom), equipment (ordered vs. merely listed), the
  "when to call" page, and the admin tail.
- `docs/06-homecoming.md` — the first-night plan, the house audit,
  the recovery week at household scale, and wind-down planning.
- `docs/07-bill-review.md` — the bill-review step: the four
  envelopes, the dates-match and providers-match checks, the one
  hospital call worth making, and the three-pen review ritual. Hands
  the baton to the *medical-bills-comfort-guide*.
- `docs/08-glossary.md` — plain-words glossary (forms, people,
  room shorthand, bill paper), with the standing rule that
  definitions are vocabulary, never instructions.
- `docs/cards/packing-card.md` and `docs/cards/teach-back-card.md` —
  the two required printable one-page cards.
- `docs/disclaimer.md` — the education-only promise stated fully,
  plainly, and in the guide's one set of capital letters.
- `build.py` (+ `build.sh`) — zero-dependency Python 3 stdlib static
  site builder: Markdown → HTML with sidebar nav, print-friendly CSS
  in `assets/style.css`, and a `--check` mode that verifies every
  internal link and anchor (`build.py --check`).
- `tests/test_build.py` (+ `test.sh`) — 36 tests, described below.
- `README.md`, `LICENSE` (MIT), `.gitignore`.

Every doc carries an education-only / never-medical-advice line; the
care team is consistently named as the destination for all care
questions.

## How to run it

```bash
python3 build.py --check   # build site/ + verify all internal links
./test.sh                  # full test suite (also builds the site)
```

Then open `site/index.html` in a browser. Fully offline afterwards;
no network, accounts, or trackers. Python 3 standard library only.

## Verification results

- `python3 build.py --check` → builds all 13 pages
  (9 chapters, 2 cards, glossary, disclaimer, CSS); "Link check: all
  internal links resolve."
- `./test.sh` → **36 tests, all OK** (Ran 36 tests in ~0.1s):
  - build produces every chapter/card/glossary page plus stylesheet;
  - every page carries the nav and the education-only notices;
  - no `file://` URLs or absolute local paths in output;
  - all internal links and anchors resolve (and the checker provably
    detects a deliberately broken one);
  - converter regressions guarded (headings/IDs, paragraphs, wrapped
    list-item continuations, checkbox lists, tables, fenced code,
    blockquotes, inline bold/italic/nested emphasis, escaping, hr);
  - content guards: all goal topics present, both cards printable,
    discharge chapter covers all five parts, glossary defines key
    terms, every doc says "never medical advice";
  - repo hygiene: LICENSE copyright is exactly
    "Copyright (c) 2026 Asdale Dynamics, LLC", README credits the
    LLC, and no secret-shaped or SSN-shaped strings anywhere.
- Fixes made during this pass (found by the critically-against-goal
  review and reruns): three converter bugs — wrapped list-item
  continuations splitting into stray paragraphs, bold/italic that
  wrapped across lines staying literal, and nested
  `**bold *em* text**` emphasis not parsing (bold made lazy +
  DOTALL, and list items / paragraphs now convert once after joining
  their raw lines); plus assorted muddled sentences cleaned up and
  two docs missing the verbatim "never medical advice" line fixed.

## Known gaps

- **By design:** no medical content of any kind — symptom lists and
  treatment details are deliberately paraphrased as "the care team's
  words," not invented here. Where a hospital-specific fact varies
  (forms riders, room supplies, discharge packet shape), the text
  says so and points to asking.
- No search function or dark mode on the built site; sidebar nav
  only (consistent with sibling guides).
- Insurance/interpreter specifics are US-flavored (HIPAA, 911); other
  regions would need their own notes.
- The site is static HTML; the cards print via the browser's
  print dialog (print CSS included), not a generated PDF.
- Companion-project links (medical-bills-comfort-guide,
  free-health-admin-kit) are by name, not URL, since they are
  sibling repositories with no fixed relationship in-repo.
