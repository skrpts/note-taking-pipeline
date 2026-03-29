---
type: skill
id: content-distillation
title: Content Distillation
description: "Transforms raw, unstructured academic content into clean, organised notes using evidence-based note-taking methods"
tags: [Production, Tested, learning:comprehension, learning:synthesis]
connections:
  - target: llm-service
    type: runs_on
  - target: note-taking-methods-reference
    type: references
  - target: effective-note-taking-guide
    type: references
metadata:
  estimated_duration: "3-8 minutes"
  avg_tokens: 3000
---

## Capability

Content Distillation is the core processing skill for transforming raw academic input into structured, retrievable notes. It handles three distinct input types — lecture transcripts or notes, reading materials, and seminar discussions — and applies the appropriate structuring method to each.

This skill understands the difference between linear lecture content (which benefits from the Cornell method or outline format), argumentative academic writing (which requires extraction of claims, evidence, and reasoning), and discussion-based seminar content (which needs identification of key positions, debates, and consensus points).

## Processing Approach

### For Lecture Content
1. Identify the lecture's main topic, subtopics, and learning objectives
2. Extract key concepts, definitions, theories, and examples
3. Organise into a hierarchical structure — main headings for topics, subheadings for subtopics
4. Generate cue questions in the left margin (Cornell style) that test understanding of each section
5. Write a summary paragraph capturing the lecture's core message in the student's own words
6. Flag any points that were unclear or need follow-up

### For Reading Materials
1. Identify the text type: journal article, textbook chapter, policy document, primary source
2. Extract the central argument or thesis (for argumentative texts) or key concepts (for expository texts)
3. Pull out supporting evidence, data, and examples
4. Note methodological approaches and their strengths or limitations
5. Capture direct quotations that are particularly well-expressed or important (with page references)
6. Generate questions the reading raises or leaves unanswered
7. Identify connections to other materials the student has encountered

### For Seminar Discussions
1. Identify the core questions or themes discussed
2. Capture the main positions or arguments raised by participants
3. Note areas of agreement, disagreement, and unresolved debate
4. Extract any new references, readings, or resources mentioned
5. Record personal insights or questions that arose during discussion

## Quality Criteria

- Notes must be in the student's voice, not copied verbatim from the source (unless quoting)
- Every section must have at least one cue question or retrieval prompt
- Technical terms must be defined on first use
- The summary must be concise enough to read in under 60 seconds
- Connections to prior knowledge should be flagged with a "Link:" prefix
- Unclear points should be flagged with a "Follow-up:" prefix

## Constraints

- Do not fabricate information not present in the source material
- Preserve the author's original meaning when paraphrasing
- If the input is too short or vague to produce meaningful notes, request clarification rather than padding
- Maintain academic register appropriate to the subject area
- Do not impose a structure that does not fit the content — adapt the method to the material
