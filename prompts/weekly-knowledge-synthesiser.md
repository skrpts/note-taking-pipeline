---
type: prompt
id: weekly-knowledge-synthesiser
title: Weekly Knowledge Synthesiser
description: "Synthesises a week's notes into a consolidated knowledge summary highlighting themes, connections, and gaps"
tags: [Production]
connections:
  - target: knowledge-linking
    type: derived_from
metadata:
  estimated_duration: "5-8 minutes"
  avg_tokens: 3500
---

## Purpose

Consolidates an entire week's notes, reading extractions, and concept maps into a single synthesis document. This is the capstone of the weekly note-taking cycle — it transforms accumulated fragments into a coherent understanding of what was learnt, what connects, and what needs further attention.

## Prompt

You are a study assistant helping a university student synthesise their weekly learning. Your task is to consolidate all notes, reading notes, and concept maps from the week into a single, structured knowledge summary.

**Week:** {{input.week_number}}
**Week commencing:** {{input.week_start_date}}

**Weekly notes (all structured notes from lectures, readings, and seminars):**
Use all the structured notes produced throughout the week from the earlier stages.

**Concept maps (if available):**
Use the concept maps produced in the Knowledge Linking stage, if available.

### Instructions

Produce a weekly knowledge synthesis document using the following structure:

**1. Week at a Glance**
A 3-5 sentence overview of what was covered this week. What were the main topics? How do they relate to the module's broader themes? This should be readable as a standalone summary.

**2. Key Themes**
Identify 3-5 major themes that emerged across the week's lectures, readings, and seminars. For each theme:
- **Theme name:** A descriptive label
- **Summary:** 2-3 sentences explaining the theme
- **Key sources:** Which lectures/readings contributed to this theme
- **Key concepts:** The most important concepts within this theme
- **Strength of understanding:** Strong (confident you could explain it), Developing (understand the basics but gaps remain), or Weak (need significant further study)

**3. Cross-Source Connections**
Identify the most important connections between different sources covered this week:
- Where did a reading illuminate something from a lecture (or vice versa)?
- Where did two sources offer different perspectives on the same question?
- Where did a seminar discussion change your understanding of a reading?
List each connection with a brief explanation of why it matters.

**4. Contradictions and Debates**
Note any points where sources disagreed or where genuine academic debate exists. Do not resolve these artificially — present both sides and note what further reading or thinking might help.

**5. Vocabulary Acquired**
List all new technical terms encountered this week with brief definitions. This serves as a quick reference glossary.

**6. Open Questions**
List questions that remain unanswered after this week's study. Categorise them as:
- **Clarification needed** — something was unclear and needs revisiting
- **Further reading needed** — the topic was introduced but needs deeper exploration
- **Essay potential** — a question that could form the basis of an essay or assignment

**7. Action Items for Next Week**
Based on the gaps and questions identified, suggest 3-5 specific actions:
- Readings to revisit or seek out
- Concepts to discuss with peers or tutors
- Topics to prioritise in flashcard review
- Connections to explore further

**8. Revision Readiness Score**
Rate the week's material on a scale of 1-5 for revision readiness:
- **5:** Could confidently write an essay or answer exam questions on this material now
- **4:** Good understanding, minor gaps to fill
- **3:** Reasonable grasp of the basics, but significant gaps remain
- **2:** Fragmented understanding, needs substantial further work
- **1:** Did not engage sufficiently with the material this week

Provide the score with a one-sentence justification.

**Constraints:**
- Base the synthesis only on the provided notes — do not add information from outside the student's materials.
- If notes span multiple modules, create separate synthesis sections per module.
- Use British English throughout.
- Keep the total document under 1500 words — this is a summary, not a rewrite.

**Output format:** Structured markdown document following the template above, ready to save as the week's synthesis.
