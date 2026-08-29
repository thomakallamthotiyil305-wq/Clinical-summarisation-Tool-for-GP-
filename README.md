# CarePath — Clinical Summarisation Tool for GP (Prototype)

A clinician-in-the-loop primary care companion prototype: transparent symptom triage, a GP consultation review pipeline with source-linked drafts and status-tracked actions, evidence-based medication information, pharmacy tracking, and calendar reminders.

**This is an illustrative, self-contained HTML/CSS/JS prototype using entirely fictional, synthetic patients. It is not a medical device, is not connected to any real clinical record, and must not be used with real patient data.**

## View it

Open [`index.html`](index.html) directly in a browser, or enable **GitHub Pages** for this repo (Settings → Pages → Deploy from branch `main` / root) to get a shareable live link.

## What it demonstrates

Three synthetic patients walk through the three outcomes a real triage/documentation tool has to get right:

- **Maya** (persistent headache) — routine/urgent triage → books a GP appointment → full clinician-in-the-loop pipeline: transcript → AI-draft summary → AI-draft actions → GP review/approval → unlocked patient summary, medication info, lab test and pharmacy next steps.
- **Jonah** (crushing chest pain, breathless) — red-flag triage → routed straight to "call 999 / go to A&E", GP booking is never offered.
- **Priya** (sore throat, mild fatigue) — no red/amber flags → shown self-care is enough, without needing a GP consultation at all.

## Why it's built this way

The design follows a critical review of the AI clinical-documentation literature (Draper et al. 2025; Williams et al. 2025; Asgari et al. 2025; Ohde et al. 2026, among others) and supervisory advice recommending a clinician-in-the-loop design using synthetic data only, rather than an autonomous system that decides what a patient "needs." Key mitigations built into the prototype:

| Evidence finding | Design response |
|---|---|
| Omissions dominate over hallucinations in AI summaries, and are harder to catch on review | Every draft line is source-linked to a transcript quote; nothing enters a record unreviewed |
| The Plan/action section is the highest-risk zone — tentative talk gets over-committed into firm actions | Explicit status taxonomy: Discussed → Proposed → Confirmed — never defaults to "done" |
| Tools must never autonomously decide what a patient "needs" | Triage is a transparent, deterministic checklist — not free-text AI judgement — and always defers to 999/A&E for red flags |
| Governance for consent, retention and audit trails is often unspecified | Prototype uses only synthetic patients; every status change is visible, nothing is sent externally |
| Overreliance risks automation bias and loss of clinician synthesis skills | The patient-facing summary is hard-locked until a clinician approves every action |

The in-app **Safety & Evidence Base** tab documents this mapping in full, plus an honest list of what the prototype does *not* solve (EMR/GP Connect integration, formal clinical risk assessment under DCB0129/DCB0160, MHRA software-as-a-medical-device classification, multiparty/non-English consultation accuracy, real consent flows).

## Known limitations

This build is illustrative, not a substitute for the systematic scoping review recommended as the actual first research deliverable before any live clinical prototype is developed. See the project documentation for the full critical analysis this prototype is grounded in.

## Stack

Single self-contained `index.html` — vanilla HTML/CSS/JS, no build step, no dependencies, no backend. State lives in memory only and resets on page reload.
