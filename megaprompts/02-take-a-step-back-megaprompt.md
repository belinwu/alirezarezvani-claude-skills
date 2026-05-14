# Mega Prompt: Take-A-Step-Back Reflection Skill

## Role

You are a **Skill Architect** specializing in metacognitive and reflection workflows. Generate a production-grade, distributable Claude skill that performs honest mid-conversation reassessment — a deliberate zoom-out from detail-mode to check direction, assumptions, and bias.

## Output Target

Single file: `${SKILLS_DIR}/take-a-step-back/SKILL.md`

Word budget: 1,400–1,800 words. Hard ceiling: 2,000.

## Skill Purpose

When invoked mid-conversation, this skill pauses execution and produces a frank reassessment of where the conversation has been heading. Output is a flowing analysis (no headers, conversational tone) covering macro perspective, gap analysis, reflective inquiry, bias check, and contextual alignment. The skill ends with a clear directional recommendation: continue, pivot, or pause to answer a specific question.

## Required Capabilities

The skill must specify how to:

1. **Recognize invocation** — Both explicit phrases and implicit signals (e.g., 10+ turns of detail work, signs of frustration, repeated dead-ends).
1. **Re-read full conversation** — From the original goal forward, not just recent turns.
1. **Perform 5-dimension analysis** — Macro, Gap, Reflective, Bias, Contextual.
1. **Deliver honest assessment** — No softening, no manufactured problems if things are on track.
1. **Issue clear directional recommendation** — Continue / Pivot / Pause for question.

## Workflow Structure

The generated skill must follow this structure:

```
1. Invocation triggers (explicit + implicit signals)
2. Stop directive (halt current thread before reassessing)
3. The 5-dimension analysis framework
   3.1 Macro Perspective
   3.2 Gap Analysis
   3.3 Reflective Inquiry
   3.4 Bias Check
   3.5 Contextual Alignment
4. Tone and format rules
5. Closing recommendation requirement
```

## Critical Improvements Over Naive Implementation

The skill MUST address these concerns:

1. **No personal references** — The original referenced a specific name (“Paul”). Strip all of these. Use second-person (“you”, “the user”) generically.
1. **Generic context applicability** — Don’t tie examples to a single domain (YouTube, AI, creator economy). Use neutral language so the skill works for any user in any context.
1. **Implicit invocation signals documented** — The skill should trigger not only on explicit phrases but on conversational patterns: extended detail focus without strategic check-in, repeated dead-ends, signs of stuck or frustrated user.
1. **Honest output discipline** — Explicit instruction NOT to manufacture problems when things are genuinely on track. Saying “this is solid because X” is a valid output.
1. **Conversation re-read requirement** — The skill must explicitly halt the current thread and re-read from the top of the conversation, not just recent turns.
1. **Format discipline** — Output is flowing prose without headers, not a structured report. This must be enforced in the skill.

## The 5-Dimension Analysis Framework (Must Be Fully Specified)

Each dimension must be documented with concrete prompting guidance:

### 1. Macro Perspective

- Original goal: What did the user actually start trying to do?
- Drift detection: Has the conversation moved away from that goal? Toward something better or worse?
- Connection check: How does current work connect to the larger objective?

### 2. Gap Analysis

- Unverified assumptions
- Missing stakeholders / audiences / users
- Skipped constraints (technical, regulatory, resource)
- Dismissed alternatives
- External factors (timing, market, dependencies)

### 3. Reflective Inquiry

- Is the problem framed correctly?
- Solving the right problem vs. adjacent easier one?
- Simpler path being overcomplicated?
- Harder but more valuable path being avoided?
- Fresh-eyes perspective: would someone else approach this differently?

### 4. Bias Check

Document these 5 biases with examples of how they manifest:

- Confirmation bias
- Sunk cost fallacy
- Anchoring
- Complexity bias
- Recency bias

For each: how to recognize it in the conversation pattern.

### 5. Contextual Alignment

- Does the direction serve the user’s actual goals (as known from context)?
- Are external factors being ignored?
- Is this the best use of the user’s time and energy right now?
- Connection to other known projects or priorities?

## Output Format Spec

The skill must produce:

- **Flowing prose**, no headers, conversational tone
- **Tight but thorough** — neither a one-liner nor a wall of text
- **Direct critique** when warranted, with specific evidence from the conversation
- **Validation** when warranted, with specific reasoning for why the path is solid
- **Closing recommendation**: Continue (and why) / Pivot (and to what) / Pause (and for which question)

## Trigger Phrases (for frontmatter description)

Explicit:

- “take a step back”
- “step back”
- “zoom out”
- “are we missing something”
- “bigger picture”
- “what are we missing”
- “let’s pause”
- “sanity check this”
- “are we on track”
- “are we overthinking this”
- “forest for the trees”

Implicit (recognized but not requiring trigger phrase):

- Conversation has gone 10+ turns deep on implementation details without strategic check-in
- User shows signs of frustration or stuck-ness
- Repeated dead-ends or pivots within a short span

## Error Handling Requirements

|Situation                                               |Behavior                                                      |
|--------------------------------------------------------|--------------------------------------------------------------|
|Conversation is very short (no real context to reassess)|Acknowledge limitation, ask user what they want reassessed    |
|Current direction is genuinely solid                    |State this clearly with reasoning; don’t manufacture problems |
|User invokes mid-task with no clear question            |Default to macro perspective + bias check; offer to dig deeper|
|Implicit trigger seems possible but unclear             |Don’t invoke proactively; ask user if they want to step back  |

## Portability Requirements

- **Claude Code CLI**: Works natively — pure reasoning skill, no external tools required.
- **Claude.ai web**: Works natively — same reasoning skill.

This skill is the most portable in the collection. No special notices needed.

## Frontmatter Spec

```yaml
---
name: take-a-step-back
description: "Mid-conversation reflection skill that pauses execution and zooms out from detail-mode to honestly reassess direction, assumptions, and bias. Use when the user says 'take a step back', 'step back', 'zoom out', 'are we missing something', 'bigger picture', 'sanity check this', 'are we on track', 'are we overthinking this', 'forest for the trees', or any variation signaling intent to break out of detail-mode and reassess. Also trigger when the conversation has gone deep on implementation details without strategic check-in, or when the user shows signs of being stuck — that's often a signal the framing needs a reset, not more detail work."
---
```

## Anti-Patterns To Reject

- Hardcoded user names or specific domain references
- Structured report output (headers, bullet lists) when prose is required
- Manufactured problems when things are actually fine
- Vague reassurance (“looks good!”) instead of specific reasoning
- Reassessing only recent turns instead of the full conversation
- Skipping the closing directional recommendation

## Validation Checklist (Run Before Delivery)

- [ ] Frontmatter parses as YAML
- [ ] Word count 1,400–2,000
- [ ] No personal names anywhere in the skill body
- [ ] All 5 dimensions documented with concrete guidance
- [ ] 5 cognitive biases explicitly listed with recognition cues
- [ ] Output format spec enforces prose-only (no headers)
- [ ] Honest-output discipline documented (don’t manufacture problems)
- [ ] Implicit invocation signals documented
- [ ] Closing recommendation requirement stated clearly
