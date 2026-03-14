---
type: skill
id: spaced-repetition-design
title: Spaced Repetition Design
description: "Designs effective flashcards and retrieval practice materials using evidence-based spaced repetition and active recall principles"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: note-taking-methods-reference
    type: references
metadata:
  estimated_duration: "3-6 minutes"
  avg_tokens: 2500
---

## Capability

Spaced Repetition Design creates flashcards and retrieval practice materials that maximise long-term retention. It applies evidence-based principles from cognitive science — the testing effect, desirable difficulty, interleaving, and elaborative interrogation — to produce cards that genuinely test understanding rather than encouraging shallow memorisation.

This skill understands that not all flashcards are equal. A card that asks "What year was X?" tests simple recall. A card that asks "Why did X lead to Y, and what alternative outcomes were possible?" tests comprehension, analysis, and application. This skill produces cards across Bloom's taxonomy levels appropriate to the material.

## Card Design Principles

### The Minimum Information Principle
Each card should test exactly one idea. If a card requires the student to recall multiple unrelated facts, split it. Complex ideas are broken into atomic components, each with its own card, then linked through related card sequences.

### Desirable Difficulty
Cards should be challenging enough to require genuine retrieval effort but not so difficult that the student cannot answer them within 15-30 seconds of thought. Difficulty is calibrated by:
- Adjusting the specificity of the question
- Providing or withholding contextual cues
- Varying the response format (definition, explanation, comparison, application)

### Card Types
1. **Definition cards** — "What is X?" / concise definition. Used sparingly for essential terminology.
2. **Explanation cards** — "Explain why X occurs" / 2-3 sentence explanation. Tests comprehension.
3. **Comparison cards** — "How does X differ from Y?" / structured comparison. Tests analysis.
4. **Application cards** — "Given scenario Z, how would you apply X?" / worked application. Tests transfer.
5. **Elaborative interrogation cards** — "Why is the statement X true?" / reasoned justification. Tests deep understanding.
6. **Cloze deletion cards** — key terms removed from a statement. Used for definitions and processes.

### Tagging and Metadata
Every card is tagged with:
- **Topic** — the subject area or module section
- **Difficulty** — beginner, intermediate, or advanced
- **Bloom's level** — remember, understand, apply, analyse, evaluate, or create
- **Source** — which note or reading the card was derived from

## Quality Criteria

- No card should be answerable by pattern matching or keyword recognition alone
- Every "back" answer should be self-contained — a student seeing only the answer should understand it
- Cards derived from the same concept should be interleaved with cards from other topics
- The set should include at least 30% higher-order cards (apply, analyse, evaluate) for university-level material
- Avoid cards that test trivial or easily looked-up facts unless those facts are foundational

## Constraints

- Never create cards that test information not present in the source notes
- Do not exceed the requested card count — quality over quantity
- If the source material is insufficient for the requested number of cards, produce fewer cards and explain why
- Avoid negatively phrased questions ("Which of the following is NOT...") as they test recognition, not recall
- All cards must be in the student's language and register, not copied verbatim from source texts
