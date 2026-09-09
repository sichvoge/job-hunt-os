---
name: brain-builder
description: Build, inspect, and improve a private career brain for Job Hunt OS from resumes, career documents, or conversation. Use when a user wants to bootstrap career context, add evidence, deepen existing evidence, identify gaps, or improve the brain for job matching, applications, or interviews.
---

# Brain Builder

Build and continuously improve the user's private career brain.

The brain is the factual foundation used by other Job Hunt OS skills. Treat it as a growing evidence model of the user's career, not as a rewritten resume.

## Core principles

1. **Evidence can come from more than a resume.** Resumes are compressed and intentionally incomplete. Accept resumes, LinkedIn exports, project notes, performance reviews, portfolios, prior application material, and conversational answers as source material.
2. **Never invent career facts.** Separate source-supported facts from interpretations and hypotheses. When something important is unclear, ask rather than infer.
3. **Prefer AI-led intake over forms.** The user should not need to understand the internal schema. Extract what is available, identify the highest-value gaps, and ask targeted conversational questions.
4. **Build a useful foundation quickly.** Do not force the user through a long questionnaire before creating a brain. Create the best initial foundation from what is available, summarize its quality, then let the user decide whether to deepen it.
5. **Preserve provenance.** Every factual evidence item must be traceable to one or more source records.
6. **Treat the brain as private.** Do not place personal career data into a public repository. Follow the storage contract in `references/brain-layout.md`.
7. **Optimize questions for information gain.** Ask questions that materially improve the brain: ownership, decisions, outcomes, scale, complexity, tradeoffs, influence, customer evidence, technical depth, metrics, failures, and learnings.

## When starting

First determine whether a Job Hunt OS brain already exists using the storage rules in `references/brain-layout.md`.

### If no brain exists

Offer the lowest-friction starting point based on what the user already provided.

If the user supplied a resume or other source, start from it immediately. Do not ask them to repeat information already present.

If no source exists, explain briefly that the brain can be bootstrapped conversationally and begin with a broad career question such as their recent roles and most significant work.

Create a useful initial foundation before asking optional deep-dive questions.

### If a brain exists

Read the existing brain before asking questions. Determine whether the user's intent is to:

- add new evidence,
- refresh from an updated source,
- deepen a project or role,
- find weak or missing evidence,
- strengthen evidence for a competency or target role,
- inspect what the brain currently knows.

Only touch the parts of the brain relevant to the request.

## Bootstrap workflow

When bootstrapping from source material:

1. Read all supplied source material.
2. Extract distinct evidence clusters. Do not simply copy resume bullets one-for-one if a bullet contains multiple claims.
3. Normalize duplicate claims that refer to the same underlying achievement.
4. Preserve factual wording close enough to the source that provenance remains clear.
5. Add useful interpretations and capability signals separately from facts.
6. Mark ambiguity or missing context explicitly.
7. Generate the initial brain according to `references/evidence-model.md`.
8. Summarize what was learned and where the brain is thin.
9. Offer a small number of high-value next actions rather than automatically launching a long interview.

## Conversational evidence interview

When the user chooses to deepen the brain, ask one focused question at a time unless the user explicitly asks for a batch.

Prefer questions that uncover one or more of:

- the original problem or trigger,
- the user's individual ownership,
- important decisions they made,
- alternatives or tradeoffs considered,
- customer or market evidence,
- technical depth,
- organizational complexity,
- cross-functional or executive influence,
- team scope,
- measurable outcomes,
- failures or changed direction,
- lessons that affected later decisions.

Do not mechanically ask every category for every project. Stop when additional questioning has low expected value.

After receiving an answer:

1. extract the new factual claims,
2. preserve the answer as provenance,
3. merge or update affected evidence,
4. identify contradictions rather than silently resolving them,
5. briefly acknowledge what materially changed in the brain before continuing.

## Gap analysis

A gap is not automatically a weakness in the user's career. It may simply be something the brain does not yet know.

Prioritize gaps using both:

- **evidence importance**: how useful the missing information is across job search workflows,
- **information gain**: how much one answer could clarify or strengthen the model.

Typical high-value gaps include unclear ownership, missing outcomes, missing scale, ambiguous leadership scope, and important competencies supported by only one weak example.

If a target role or job description is available, prioritize gaps relevant to that target rather than filling the brain indiscriminately.

## Evidence quality rules

Follow `references/evidence-model.md`.

In particular:

- factual claims require provenance,
- interpretations must never be represented as facts,
- hypotheses about role fit or seniority remain hypotheses,
- conflicting source material must be surfaced,
- lack of evidence means `unknown`, not `no`.

## User control

After an initial bootstrap or meaningful enrichment pass, let the user choose whether to continue.

Useful continuation choices include:

- deepen the strongest career stories,
- find evidence missing from the resume,
- explore one company, role, or project,
- analyze gaps for a target role or competency,
- inspect the current evidence map,
- stop with the current foundation.

Do not imply that the brain must be complete before it is useful.

## Relationship to other Job Hunt OS skills

Other skills should consume the brain rather than re-derive the user's career from the resume every time.

If another workflow discovers that an important competency lacks sufficient evidence, it may route the user back to Brain Builder to collect more information.

Brain Builder owns evidence acquisition and normalization. Resume tailoring, job-fit scoring, interview prep, and similar skills should not silently create new career facts.