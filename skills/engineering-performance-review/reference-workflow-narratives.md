# Workflow: narratives and plans (reference)

### Step 1 — Ingest and Map

Read the competency framework carefully. For each competency:
- Identify the mastery levels and their observable behaviours
- Note the expected level for the engineer's seniority (from the grading matrix if provided)

Then read the self-assessment. For each competency:
- Note the level the engineer claims
- Extract the specific examples they provide as evidence
- Flag where examples are vague, missing, or don't clearly map to the claimed level

**Self-assessment quality check (meta-signal):**

The quality of the self-assessment is itself evidence — particularly for Leadership (self-awareness)
and Autonomy (ability to reflect honestly on own performance). Evaluate each self-assessment on:

| Dimension | Weak signal | Strong signal |
|---|---|---|
| Specificity | Vague assertions ("I did good work on X") | Concrete examples with context, actions, and outcomes |
| Outcome orientation | Lists activities ("I built Y") | Cites measurable outcomes ("Y improved metric Z by N%") |
| Self-awareness | Every competency rated at or above level; no gaps acknowledged | Honest acknowledgment of areas still developing |
| Reflection depth | Reads like a checklist / copy-paste of rubric language | Shows genuine analysis of own growth, struggles, and learning |

Note the quality assessment in the calibration table. An engineer who writes a thoughtful,
honest self-assessment with specific evidence and acknowledged gaps is showing different maturity
than one who inflates every competency with vague assertions — even if the underlying performance
is similar.

### Step 2 — Calibration Analysis

Before writing any assessments, produce a calibration table:

```
Competency | Self-rated | Expected for level | Your initial read | Confidence | Key question
```

- **Self-rated**: What the engineer claimed
- **Expected for level**: What the rubric says their seniority should be at
- **Your initial read**: Your provisional view based on evidence so far
- **Confidence**: High / Medium / Low (Low = you need more evidence)
- **Key question**: What would change your rating up or down?

Flag any competency where:
- Self-rating is more than one level above your initial read (potential inflation)
- Self-rating is more than one level below your initial read (potential underselling)
- You have Low confidence (evidence gap — needs investigation or peer input)

**Handling material discrepancies between self-assessment and evidence:**

A material discrepancy is when your rating and the engineer's self-rating differ by one full
mastery level or more. This requires careful handling:

- **Do not soften your rating to reduce the gap.** The manager assessment must reflect your
  honest evidence-based view. Softening it to match the self-assessment defeats the purpose
  of the review and sets false expectations.
- **Do document the gap explicitly** in the discrepancy field of the competency assessment,
  with the specific reasoning for why the evidence does not support the self-rated level.
- **Frame for the alignment 1:1:** When a significant gap exists, suggest to the manager how
  to open the conversation. A useful frame is: "I want to share my read of [competency], and
  I'd like to understand what you were drawing on when you rated yourself [level] — because
  I may have missed something." This invites dialogue rather than delivering a verdict.
- **Distinguish underselling from inflation:** An engineer who undersells themselves (rates
  lower than evidence supports) needs encouragement and visibility into their own strengths.
  An engineer who oversells needs honest, specific feedback about the gap — with concrete
  examples of what the next level actually requires, not just an assertion that they're not there.

### Step 2b — Manager Validation (before writing any assessments)

After completing the calibration table, **stop and present it to the manager** for validation
before writing a single competency narrative. This is a mandatory checkpoint.

Present the calibration table and ask:

```
Here is my provisional calibration for [Engineer Name] based on all evidence gathered.
Before I write the full assessment, I want to check two things:

1. Do any of these provisional ratings look wrong to you — either too high or too low?
   If so, what are you seeing that I might have missed?

2. Is there anything in your own notes or observations from this review period that
   I haven't captured? For example:
   - Specific moments that stood out (positively or negatively)
   - Context that changes how an example should be interpreted
   - Behaviours you've observed directly that aren't visible in the wiki or work tracker
   - Anything that happened outside the formal record

Even brief bullet points are useful. I'd rather incorporate your perspective now
than correct it in the alignment conversation with the engineer.
```

Wait for the manager's response before proceeding. This step exists because:
- The manager has direct observation that no artifact can capture
- A calibration error caught before writing is far less damaging than one caught after
- The manager may have context that changes the interpretation of an evidence gap
  (e.g. "that ticket stalled because I asked them to pause, not because they were blocked")

If the manager confirms the calibration looks right and has nothing to add, proceed to Step 3.
If they flag a discrepancy or add new information, update the calibration table accordingly
before writing.

### Step 3 — Manager Assessment (write only after Step 2b confirmed)

#### Step 3a — Outcome Summary (write this first, before competencies)

Before writing any competency assessment, produce a brief **Outcome Summary** that anchors
the entire review in what actually shipped and landed during the review period. This section
answers: "What changed for users, the system, or the team as a direct result of this
engineer's work?"

Structure:

```
## Outcome Summary — [Review Period]

**What shipped and landed:**
- [Initiative] — [1-sentence description of what changed and for whom]
- ...

**What was started but not yet landed:**
- [Initiative] — [current status and why it hasn't landed]

**What didn't go well:**
- [Initiative or pattern] — [1-sentence description of the issue and its impact]
```

Guidelines:
- **Outcomes, not activities.** "GCP migration completed, reducing deploy time from X to Y"
  is an outcome. "Worked on GCP migration" is an activity. Push for outcomes wherever possible.
  When an outcome metric isn't available, describe the observable state change ("the platform
  now has X capability that didn't exist before").
- **Include work that didn't land.** This is not punitive — it provides honest context.
  Significant effort invested in work that was subsequently paused, descoped, or didn't deliver
  the expected result should be noted with the reason (requirements gap, deprioritised, blocked).
- **"What didn't go well" is about patterns, not blame.** Name production issues, rework
  cycles, or efficiency gaps factually. These will be explored in the competency assessments.
- **Keep it to 150–250 words.** This is a grounding device, not a comprehensive project log.
  Cover the 3–5 most significant workstreams.

This section appears at the top of the written assessment, before the calibration summary
table and competency narratives. Its purpose is to ensure both the manager and engineer
are grounded in what actually happened before discussing mastery levels.

#### Step 3b — Per-Competency Assessments

**Role-specific framing for platform / internal-tooling engineers:**

When writing assessments for platform or shared-services roles, reframe competency evidence to match
the role’s value delivery model (names on the rubric may differ by org):
- **Impact**: Reliability, cost, toil reduction, internal adoption, onboarding time, support-ticket
  trends — not only end-user product metrics
- **Craftsmanship**: Infra-as-code, pipeline quality, observability, incident handling — match signals
  to what the role actually ships
- **Architecture**: Systems for reliability, scale, and internal developer experience — as defined in the rubric
- **Leadership**: Feedback from internal customers (feature teams, SRE, etc.) on quality and responsiveness

**Confidence language — calibrate your certainty in the narrative:**

| Confidence level | Language to use |
|---|---|
| High | "Consistently demonstrates…" / "Clear pattern of…" / "Repeatedly observed…" |
| Medium | "Evidence suggests…" / "Based on available examples…" / "Emerging pattern of…" |
| Low | "Provisional — limited evidence…" / "Not yet sufficiently evidenced…" |

For each competency, write a structured assessment block:

```
[COMPETENCY NAME]
Rating: [MASTERY LEVEL]
Expected for seniority: [MASTERY LEVEL]
Confidence: [High / Medium / Low]

Key evidence:

| # | Source | Date | Evidence summary | Link |
|---|--------|------|------------------|------|
| 1 | [GitHub / wiki / tracker / chat / Peer / Manager] | [Date] | [1-2 sentence factual description] | [Link if available] |
| 2 | ... | ... | ... | ... |

Include 3–7 evidence items per competency. For each item:
- Classify as: ⬇️ Below level / ✅ At level / ⬆️ Above level
- Cite the specific source (PR number, wiki page, ticket id, peer name)
- Link to the artefact where possible — traceability builds trust in tough conversations

Rubric coverage:
For each observable behaviour listed in the rubric at the expected mastery level,
assess coverage:
- [Rubric behaviour 1] — Met / Partially met / Not evidenced
- [Rubric behaviour 2] — Met / Partially met / Not evidenced
- ...

Behavioural patterns:
Where 2+ evidence items point to the same underlying behaviour, name the pattern
explicitly and cross-reference the evidence items that form it. Use these labels:
- "Pattern (N instances)" — consistently observed, high confidence
- "Tendency (N instances)" — emerging, moderate confidence
- "One instance observed" — noted but cannot generalise

Example: "Scope-dependent quality (pattern, 3 instances): Smaller, focused changes
(items #3, #5) are consistently clean. Larger features (#1, #2) have production
readiness gaps. References: C1, C2, C5."

Patterns are more useful for development planning than individual examples because
they give the engineer a mental model to work with, not just a list of things to fix.

Evidence supporting this rating:
- [Specific example 1 — what happened, what they did, what the outcome was]
- [Specific example 2]

Where they are relative to the next level:
- [What behaviours are present that signal upward movement]
- [What is still missing or inconsistent to reach the next level]

Discrepancy with self-assessment (if any):
- [Note if your rating differs from theirs, and why]
```

Write each competency independently. Do not let your view on one influence another.

**Scaling evidence depth to the situation:**

Not every review requires the same level of evidence granularity. Use this guide:

| Situation | Evidence table depth | Rubric coverage |
|---|---|---|
| Rating matches self-assessment, no concerns | 3–4 key items, links optional | Brief — note any "not evidenced" bullets only |
| Rating differs from self-assessment by 1 level | 5–7 items with links | Full — assess every rubric bullet |
| Rating is below expected for seniority | 5–7 items with links | Full — this is the defensibility case |
| Underperformance or at-risk signals | Comprehensive with links | Full — document the evidence trail |

The evidence table is most valuable when it needs to be defensible — contested ratings,
underperformance, or calibration discussions. For straightforward "at level, no surprises"
competencies, a lighter touch is appropriate.

### Step 4 — Overall Assessment

After all competencies, write a brief overall summary covering:

1. **Current performance level**: What level are they demonstrably performing at, overall?
2. **Promotion readiness** (if relevant): Are they performing at the next level consistently, or only in moments?
3. **Trajectory**: Are they improving, plateauing, or showing signs of decline? What's the evidence?
4. **Standout strength**: One specific thing they do exceptionally well
5. **Most important growth area**: The single highest-leverage thing they should focus on next

Between the standout strength and most important growth area, include a **Decision Ownership**
summary if the evidence supports it — particularly useful for Autonomy assessment:

```
Decision ownership:
| Work | Who initiated? | Engineer's role |
|------|---------------|-----------------|
| [Initiative] | [Self / Squad-planned / Manager-directed] | [Brief description of ownership scope] |
```

This table makes self-direction visible at a glance. For engineers at Senior+ level,
a high proportion of self-initiated work is a strong Autonomy signal. For engineers
where Autonomy is a concern, the table may reveal that most work was assigned rather
than identified. Include only the 4–6 most significant workstreams, not every ticket.

Keep this to ~150 words. It should be usable verbatim in a review conversation.

6. **Evidence gaps**: Name the specific evidence that, if obtained, would confirm or change
   a rating. This is not a weakness — it is intellectual honesty about the assessment's limits.
   Structure as:

   ```
   Evidence gaps:
   - [Competency]: [What's missing and what it would change]
     Example: "Impact: deployment validation for the failover client would move this
     from Partially met to Clearly met on the 'delivers complex systems' rubric bullet."
   - [Competency]: [What's missing]
   ```

   Include only gaps that would materially affect a rating — not everything you wish you had.
   This section serves two purposes: (a) it tells the engineer what they could do to
   strengthen their case in the next cycle, and (b) it protects the manager if a rating
   is later challenged — the limits of the evidence were stated upfront.

### Step 5 — Development Plan

Generate a focused development plan. Do not list everything — prioritise ruthlessly.

```
DEVELOPMENT PLAN — [Engineer Name / Role]

Focus period: [e.g. Next 6 months]

Priority 1: [Competency or behaviour to develop]
  Why this: [Why this is the highest-leverage focus]
  What good looks like: [Specific observable behaviour at the next level]
  How to get there: [2-3 concrete actions — projects, behaviours, habits]
  How we'll know it's working: [What you'll look for as evidence of progress]

Priority 2: [Only if truly distinct from Priority 1]
  [Same structure]

What we're NOT focusing on this period:
  [Name 1-2 things explicitly de-prioritised, and why]
```

Limit to 2 development priorities maximum. More than 2 dilutes focus and rarely leads to meaningful change.

**When the engineer is solidly at-level with no immediate promotion path:**

Not every development plan needs to be "here's what's missing for the next level." For engineers
who are performing well at their current level but where promotion is not imminent (no headcount,
no business need, or they're early in their current level), use a deepening-focused plan:

```
DEVELOPMENT PLAN — [Engineer Name / Role]

Focus period: [e.g. Next 6 months]

Context: [Engineer name] is performing solidly at the [seniority] level. This plan focuses
on deepening mastery and expanding capability within the current level rather than
progression to the next level.

Priority 1: [Skill to deepen or capability to expand]
  Why this: [How this makes them more effective in their current role or builds a foundation
  for future growth]
  What it looks like: [Specific projects, stretch assignments, or skills to develop]
  How to get there: [2-3 concrete actions]
  How we'll know it's working: [Observable evidence of deeper capability]

What we're explicitly NOT framing as a gap:
  [Name things that are at-level and solid — affirm what's working, not just what's next]
```

**When the engineer is not meeting expectations at their current level:**

The standard development plan assumes the engineer is performing at or above expectations and
the goal is growth toward the next level. When an engineer is underperforming at their current
level, the plan needs a different framing and different principles:

- **Name the gap directly but constructively.** The plan should clearly state which
  competencies are below the expected level for their seniority, with specific behavioural
  examples — not vague references to "areas for improvement."
- **Focus on getting to level, not exceeding it.** The priority is demonstrating consistent
  competency at the expected level before any discussion of advancement. Frame development
  priorities around closing specific observed gaps, not stretch goals.
- **Set a shorter feedback loop.** Rather than a 6-month horizon, establish a 4–6 week
  checkpoint to review specific observable behaviours. Name what you will look for and when.
- **Be explicit about stakes where appropriate.** If underperformance is putting their role
  at risk, the skill should flag this to the manager — the development plan should reflect
  the seriousness of the situation, not soften it. The manager must decide whether to include
  this framing in the alignment conversation, but the assessment should make it visible.
- **Separate cause from symptom.** Before assigning a low rating, consider whether the gap
  reflects capability, context, or circumstance. An engineer new to a role, working through
  a difficult team period, or taking on a domain stretch may show lower-than-expected
  performance for reasons that don't reflect their ceiling. Note this where relevant.

Template for underperformance plan:

```
DEVELOPMENT PLAN — [Engineer Name / Role]
Focus period: Next 6–8 weeks (shortened review cycle — see note below)

Context: [Engineer name] is currently performing below the expected level for [seniority]
in [competency/ies]. This plan focuses on closing that gap before addressing growth beyond
the current level.

Priority 1: [Specific competency gap]
  Current behaviour observed: [What you are seeing — specific, behavioural]
  Expected behaviour at [seniority] level: [What the rubric requires — specific]
  What needs to change: [2-3 concrete, observable behaviour changes]
  Checkpoint: [Specific date] — we will review [specific evidence] to assess progress

What we are NOT asking for right now:
  [Name stretch goals or advancement conversations explicitly de-prioritised until
  performance is consistently at level]

Note to manager: Given the performance gap, recommend a 4–6 week check-in rather
than waiting for the next formal review cycle.
```

