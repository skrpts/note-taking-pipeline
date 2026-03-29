---
type: skill
id: knowledge-linking
title: Knowledge Linking
description: "Identifies and maps connections between concepts across multiple notes, readings, and sources to build an interconnected knowledge graph"
tags: [Production, Tested, learning:comprehension, learning:synthesis]
connections:
  - target: llm-service
    type: runs_on
  - target: note-taking-methods-reference
    type: references
metadata:
  estimated_duration: "5-10 minutes"
  avg_tokens: 4000
---

## Capability

Knowledge Linking analyses a collection of structured notes and identifies the conceptual relationships between them. It produces concept maps and synthesis documents that reveal how ideas connect, contradict, support, or extend one another across different sources, lectures, and readings.

This skill draws on the Zettelkasten principle of atomic, interconnected notes. Rather than treating each lecture or reading as an isolated unit, it weaves them into a growing web of understanding that mirrors how experts think about a subject.

## Processing Approach

### Connection Identification
1. **Shared concepts** — identify terms, theories, or frameworks that appear across multiple notes
2. **Supporting evidence** — find cases where one source provides evidence for a claim made in another
3. **Contradictions** — detect where sources disagree on facts, interpretations, or conclusions
4. **Extensions** — spot where one source builds on, refines, or qualifies ideas from another
5. **Gaps** — identify questions raised in one source that are answered (or left open) in others
6. **Causal chains** — trace cause-and-effect relationships that span multiple sources

### Concept Map Construction
1. Extract the key concepts (nodes) from each note — typically 3-7 per source
2. Define the relationship type for each connection (supports, contradicts, extends, exemplifies, causes, requires)
3. Assign confidence levels to connections: strong (explicit in sources), moderate (implied), or tentative (inferred)
4. Group related concepts into clusters that represent broader themes
5. Identify bridge concepts that connect otherwise separate clusters
6. Highlight orphan concepts that have no connections — these may indicate gaps in understanding

### Synthesis Generation
1. Open with the overarching theme or question that ties the sources together
2. Present the main conceptual clusters and their internal logic
3. Discuss cross-cluster connections, especially surprising or non-obvious ones
4. Address contradictions honestly — do not resolve them artificially
5. Close with open questions and suggested next steps for study

## Quality Criteria

- Every connection must be traceable to specific content in the source notes
- Concept maps must be readable — no more than 20 nodes for a weekly synthesis
- Contradictions must be presented as such, not smoothed over
- The synthesis should reveal something the individual notes do not — it must add value beyond aggregation
- Bridge concepts should be highlighted as they are often the most valuable for deep understanding

## Constraints

- Do not invent connections that are not supported by the source material
- Do not privilege one source over another unless the student has indicated a hierarchy
- If the notes are from different modules or subjects, only link where genuine cross-disciplinary connections exist
- Keep the concept map focused on the current study period — do not try to map the entire subject
