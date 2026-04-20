---
name: b2b-client-room-reading
description: Analyze B2B client-call transcripts for stakeholder dynamics, buying intent, power maps, common questions, pressure questions, client requests, competitor mentions, jargon, answer quality, and next-call preparation. Use when founders, sales leads, PMs, operators, or service teams need to review high-consideration B2B calls in AEC, legal, professional services, technical sales, or similarly complex industries.
---

# B2B Client Room Reading

## Overview

Use this skill to turn one or more B2B client-call transcripts into an evidence-based room-reading report. The report should help a team understand who matters, what the client is really asking, how well the team answered, which commitments were made, and what to prepare before the next conversation.

Output in English only.

## Required Workflow

1. Read the full transcript before summarizing.
2. Build a speaker map from attendee metadata and transcript speaker labels.
3. Identify client-side participants, vendor-side participants, and unknown speakers.
4. Separate facts from inferences. Mark weak evidence as low confidence.
5. Extract common questions, client requests, competitor mentions, jargon, pressure questions, and implied meaning.
6. Evaluate the team's answers with the required labels: `Good`, `Watch`, `Risk`, `Do-not-answer`, or `Missing`.
7. Produce the Markdown report described in `references/report-template.md`.
8. Do not invent stakeholder authority, title, intent, or commitments.

## Input Contract

Expect the user to provide either pasted transcript text or local transcript paths.

```markdown
# B2B Client Call Input

## Transcript
[paste transcript or provide file path]

## Attendees
- Name:
  Company:
  Role/title:
  Known background:
  Speaker label in transcript:
  Client-side or vendor-side:

## Optional Context
- Deal stage:
- Industry:
- Product/service being sold:
- Known client pain points:
- Competitors or alternatives mentioned before the call:
- Internal goal for the call:
```

If attendee metadata or speaker labels are missing, still analyze the transcript, but include a missing-information note and avoid overclaiming identity, personality, or decision authority.

## Reference Loading

- Always load `references/report-template.md` before producing the final report.
- Load `references/analysis-rubric.md` for rating rules, power-map rules, confidence levels, and pressure-question handling.
- Load `references/common-questions-taxonomy.md` when categorizing repeated questions or batch patterns.
- Load `references/calibration-patterns.md` when interpreting common B2B client-call patterns.
- Load `references/anonymization-guide.md` when preparing public examples or sanitized reports.

## Analysis Rules

- Tie every recommendation to a concrete transcript signal.
- Preserve short client wording only when it reveals intent, pressure, objection, or jargon.
- Treat silence as a signal only when context supports it, such as direct questions skipped, one-word answers after pressure, or another attendee answering for the person.
- Never state that someone is the decision maker unless transcript behavior or attendee metadata supports it.
- Do not confuse talk time with authority. Analyze who asks budget, risk, approval, technical, legal, implementation, or final-decision questions.
- Capture both explicit requests and implied requests.
- Identify which questions should be answered directly, redirected, deferred, or declined.
- For competitor or alternative-tool analysis, explain why the client likely mentioned the alternative and how to position without unsupported claims.
- For jargon, separate literal wording from likely domain-specific meaning and include confidence.
- Do not provide legal, regulatory, technical, or financial advice as fact. Describe the sales-call implication and recommend appropriate verification.

## Batch Mode

When multiple transcripts are provided, produce one concise individual-call summary per call, then add cross-call sections for:

- repeated common questions,
- repeated objections,
- repeated competitor or alternative mentions,
- recurring client communication styles,
- recurring weaknesses in the team's answers,
- recommended preparation library for future calls.

## Audio Limitation

For text-only transcripts, do not infer tone, pace, interruptions, long pauses, hesitation, overlap, stress, or confidence changes. If the user provides audio-derived notes, include them in the future audio-cue section and clearly label them as audio-derived.

## Privacy

When creating public or shareable outputs, anonymize all company names, people, locations, project names, and transcript excerpts using `references/anonymization-guide.md`.
