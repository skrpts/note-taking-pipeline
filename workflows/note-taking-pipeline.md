---
type: workflow
id: note-taking-pipeline
title: Note-Taking Pipeline
description: "End-to-end workflow for structured note-taking, knowledge linking, and synthesis from lectures, readings, and seminars"
tags: [Production, Tested, Learning, Research]
connections:
  - target: content-distillation
    type: uses
  - target: knowledge-linking
    type: uses
  - target: spaced-repetition-design
    type: uses
  - target: note-taking
    type: uses
  - target: lecture-note-structurer
    type: uses
  - target: reading-note-extractor
    type: uses
  - target: concept-map-builder
    type: uses
  - target: flashcard-generator
    type: uses
  - target: weekly-knowledge-synthesiser
    type: uses
  - target: take-notes
    type: uses
  - target: llm-service
    type: runs_on
  - target: note-taking-methods-reference
    type: references
  - target: effective-note-taking-guide
    type: references
  - target: cornell-notes-template
    type: uses
  - target: weekly-synthesis-template
    type: uses
  - target: plan-studies
  - target: critical-thinking-framework
metadata:
  estimated_duration: "15-45 minutes"
  trigger: manual
    type: uses
    type: references
---

## Overview

The Note-Taking Pipeline transforms raw academic input — lectures, readings, seminars — into structured, interconnected knowledge that supports long-term retention and exam readiness. It moves through five stages: structuring raw notes, extracting key ideas from readings, linking concepts across sources, generating flashcards for active recall, and synthesising everything into a weekly knowledge summary.

## Pipeline Stages

### Stage 1: Capture and Structure

**Trigger:** After a lecture, seminar, or reading session.

Invoke the **lecture-note-structurer** prompt using the **content-distillation** skill. Feed in raw notes, recordings transcripts, or slide content. The output is a structured document following the Cornell method (or outline method, depending on user preference) with clear sections for main notes, cue questions, and a summary.

**Input:** Raw lecture notes, transcript, or slide deck content via `{{raw_notes}}`
**Output:** Structured notes document using the cornell-notes-template
**Error handling:** If input is too short (fewer than 100 words), prompt the user to add more detail or context before proceeding.

### Stage 2: Reading Extraction

**Trigger:** After completing an academic reading.

Invoke the **reading-note-extractor** prompt using the **content-distillation** skill. This stage pulls out the key arguments, supporting evidence, methodological approaches, and open questions from a reading. It produces a structured reading note that slots into the student's knowledge base.

**Input:** Reading content or summary via `{{reading_content}}`, plus `{{reading_citation}}`
**Output:** Structured reading note with arguments, evidence, and questions
**Error handling:** If the reading lacks a clear argument structure (e.g. a textbook chapter vs. a journal article), adapt the extraction to focus on key concepts and definitions instead.

### Stage 3: Knowledge Linking

**Trigger:** After accumulating 3+ structured notes from Stages 1-2.

Invoke the **concept-map-builder** prompt using the **knowledge-linking** skill. This stage identifies connections between ideas across multiple sources — shared concepts, contradictions, supporting evidence, and gaps. The output is a concept map that shows how the week's learning fits together.

**Input:** Multiple structured notes via `{{notes_collection}}`
**Output:** Concept map with nodes (concepts) and edges (relationships)
**Error handling:** If fewer than 3 notes are provided, proceed but flag that the concept map will be sparse. Suggest the student revisit after more notes are captured.

### Stage 4: Flashcard Generation

**Trigger:** After Stage 3 completes, or on demand for any structured note.

Invoke the **flashcard-generator** prompt using the **spaced-repetition-design** skill. This stage creates flashcards that test understanding rather than mere recall, using active recall principles. Cards are tagged by topic and difficulty to support spaced repetition scheduling.

**Input:** Structured notes and concept map via `{{source_notes}}`, plus `{{target_count}}`
**Output:** Set of flashcards with front/back, topic tag, and difficulty level
**Error handling:** If the source material is too narrow for the requested number of flashcards, reduce the count and explain why. Never pad with trivial or repetitive cards.

### Stage 5: Weekly Synthesis

**Trigger:** End of each study week, or before a revision session.

Invoke the **weekly-knowledge-synthesiser** prompt using the **knowledge-linking** skill. This stage consolidates all notes, reading extractions, and concept maps from the week into a single summary document. It highlights key themes, unresolved questions, and areas needing further study.

**Input:** All notes and maps from the week via `{{weekly_notes}}`, plus `{{module_name}}`
**Output:** Weekly synthesis document using the weekly-synthesis-template
**Error handling:** If the week's notes span multiple unrelated modules, produce separate synthesis sections per module rather than forcing artificial connections.

## Completion Criteria

The pipeline is complete when the student has:
1. Structured notes for every lecture and reading in the week
2. A concept map linking ideas across sources
3. A set of flashcards ready for spaced repetition practice
4. A weekly synthesis document summarising key learning

## Notes

- Stages 1 and 2 can run in parallel as notes and readings come in throughout the week
- Stage 3 benefits from having both lecture notes and reading notes available
- Stage 4 can run independently on any individual note, but produces better cards when fed the concept map as well
- Stage 5 should be the final step each week, ideally completed before the next week's lectures begin

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.module_name}}` | Yes | The module or course name | `Introduction to Sociology` |
| `{{input.raw_notes}}` | Yes | Raw lecture notes, transcript, or slide deck content | `Paste your raw lecture notes, transcript, or slide content here.` |
| `{{input.lecture_title}}` | Yes | Title of the lecture | `Social Stratification and Class` |
| `{{input.lecture_date}}` | Yes | Date of the lecture | `2026-03-18` |
| `{{input.note_method}}` | No | Preferred note-taking method (cornell or outline) | `cornell` |
| `{{input.reading_content}}` | No | Reading content or summary for extraction | `Paste the academic reading content here.` |
| `{{input.reading_citation}}` | No | Full citation for the reading | `Smith, J. (2024) 'Class in Modern Britain', Sociology Review, 12(3), pp. 45-62.` |
| `{{input.text_type}}` | No | Type of text (journal-article, textbook-chapter, etc.) | `journal-article` |
| `{{input.topic_theme}}` | No | Topic or theme for concept mapping | `Social stratification` |
| `{{input.time_period}}` | No | Time period for concept map | `this week` |
| `{{input.topic}}` | No | Topic for flashcard generation | `Social stratification` |
| `{{input.target_count}}` | No | Number of flashcards to generate | `15` |
| `{{input.difficulty}}` | No | Flashcard difficulty level | `mixed` |
| `{{input.week_number}}` | No | Week number for synthesis | `5` |
| `{{input.week_start_date}}` | No | Week commencing date for synthesis | `2026-03-16` |

## Outputs

| Name | Description |
|------|-------------|
| Structured notes document using the cornell-notes-template | Structured notes document using the cornell-notes-template |
| Structured reading note | Structured reading note with arguments, evidence, and questions |
| Concept map | Concept map with nodes  and edges |
| Set of flashcards | Set of flashcards with front/back, topic tag, and difficulty level |
| Weekly synthesis document using the weekly-synthesis-template | Weekly synthesis document using the weekly-synthesis-template |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Module Name: "Introduction to Sociology"
Raw Notes: "Today's lecture covered social stratification. Key points: Weber vs Marx on class..."
Lecture Title: "Social Stratification and Class"
Lecture Date: "2026-03-18"
```

