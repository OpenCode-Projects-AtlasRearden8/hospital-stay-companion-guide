# Hospital Stay Companion Guide

A warm, plain-English, **education-only** manual for planned and
surprise hospital stays: what to pack and what to leave home, admission
paperwork in plain words, how to be a genuinely useful bedside helper,
teach-back questions for admit and discharge conversations, the
discharge checklist decoded (meds list, follow-ups, equipment, who to
call), homecoming setup, and the bill-review step. Includes printable
one-page **packing** and **teach-back** cards and a **glossary** of the
words that show up around a stay.

**Education only, never medical advice.** Nothing in this project is
medical, legal, or financial advice. It explains forms and logistics,
not healthcare — and every page says so. For anything about actual
care, the care team is the right (and only) destination, and the guide
shows you how to ask them well.

## Why

Hospital stays arrive with clipboards, folders, and a vocabulary nobody
taught you — on weeks when your energy is already spent. This manual is
the calm friend at your elbow: plain English, step by step, never
condescending. It organizes the *around-the-stay* work so the care
conversations can happen clearly, and so discharge day doesn't ambush
anyone.

## Read it

- **On GitHub-style readers:** just open the files in
  [`docs/`](docs/index.md) — they're plain Markdown.
- **As a local website (recommended):**

  ```bash
  python3 build.py          # builds the static site into site/
  python3 build.py --check  # build + verify every internal link
  ```

  Then open `site/index.html` in a browser. Works fully offline; no
  network, no accounts, nothing leaves your machine.

## What's inside

| Part | What it covers |
| --- | --- |
| [Start Here](docs/index.md) | Two paths (planned vs. surprise) and the whole guide in eight sentences |
| [Ch. 1 — What to Pack](docs/01-packing.md) | Core list, leave-at-home list, planned-stay and scout versions |
| [Ch. 2 — Admission Paperwork](docs/02-admission-paperwork.md) | The usual folder, translated to plain words, plus the four questions worth asking |
| [Ch. 3 — Bedside Helper](docs/03-bedside-helper.md) | Journalist-and-butler role, what to collect mid-stay, the hard stops |
| [Ch. 4 — Teach-Back](docs/04-teach-back.md) | The universal opener; four playbacks at admission; the seven at discharge |
| [Ch. 5 — Discharge Checklist](docs/05-discharge-checklist.md) | Meds list, follow-ups, equipment, the call page, admin tail — each with its question |
| [Ch. 6 — Homecoming](docs/06-homecoming.md) | First-night plan, the house audit, the recovery week at household scale |
| [Ch. 7 — The Bill-Review Step](docs/07-bill-review.md) | The four envelopes, dates/providers checks, the one hospital call worth making |
| [Glossary](docs/08-glossary.md) | Plain words for the words (forms, people, room-shorthand, bill paper) |
| [Packing Card](docs/cards/packing-card.md) | One printable page for the bag — and for the scout |
| [Teach-Back Card](docs/cards/teach-back-card.md) | The opener + both question sets on one printable page |
| [Disclaimer](docs/disclaimer.md) | The education-only promise, stated fully and plainly |

## Testing

```bash
./test.sh
# or: python3 -m unittest discover -s tests -v
```

The suite builds the site, checks every internal link and anchor,
verifies all chapters/cards render with their disclaimers, and guards
against regressions in the Markdown converter — plus repo-hygiene
checks (copyright license line, LLC credit, no secret-shaped or
SSN-shaped strings). Run after any edit.

## Companion projects

- **medical-bills-comfort-guide** — what happens *after* this guide
  ends: the envelopes arrive, and bills/EOBs/deductibles get read
  calmly. This guide hands the baton over in chapter 7.
- **free-health-admin-kit** — the wider health-admin paperwork toolbox
  (insurance forms, records, appointment logs).
- Together they cover the stay, the bills, and the everyday paperwork.

## Project details

- **License:** MIT — see [LICENSE](LICENSE).
- **Copyright (c) 2026 Asdale Dynamics, LLC** of Indiana — plain-English
  AI education, books, and practical life-admin tools
  (dylanasdale.github.io, *The Massive AI Manual*).
- **Local-first and private:** static HTML built from local Markdown;
  no services, no trackers, no secrets, no personal data anywhere in
  the repo.
