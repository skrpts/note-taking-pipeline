---
type: service
id: claude-service
title: Claude Service
description: "Anthropic Claude API configuration for note-taking, knowledge synthesis, and flashcard generation tasks"
tags: [Production, Tested]
connections:
  - target: anthropic-claude
    type: depends_on
metadata:
  provider: "anthropic"
  model: "claude-sonnet"
---

## Service Configuration

This skrpt uses Anthropic Claude as its AI backbone for all note-taking, extraction, linking, and synthesis tasks. Claude's long context window and strong instruction-following make it well-suited to processing lengthy lecture transcripts, academic readings, and multi-source synthesis.

## How This Skrpt Uses Claude

### Note Structuring (Stages 1-2)
- **Task:** Transform raw notes and readings into structured documents
- **Context requirements:** Moderate (2,000-8,000 tokens of input content)
- **Temperature:** Low (0.2-0.3) for faithful restructuring without creative embellishment
- **Output length:** 500-2,000 tokens depending on input length

### Knowledge Linking (Stage 3)
- **Task:** Analyse multiple notes and identify conceptual relationships
- **Context requirements:** High (5,000-20,000 tokens when processing a week's notes)
- **Temperature:** Moderate (0.4-0.5) to allow identification of non-obvious connections
- **Output length:** 1,000-3,000 tokens for concept maps

### Flashcard Generation (Stage 4)
- **Task:** Create flashcards that test understanding at multiple cognitive levels
- **Context requirements:** Moderate (3,000-10,000 tokens of source notes plus concept map)
- **Temperature:** Moderate (0.4-0.5) to generate varied question styles
- **Output length:** 100-150 tokens per flashcard

### Weekly Synthesis (Stage 5)
- **Task:** Consolidate a full week's notes into a coherent summary
- **Context requirements:** High (10,000-30,000 tokens for a full week's material)
- **Temperature:** Low-moderate (0.3-0.4) for faithful synthesis with some interpretive licence
- **Output length:** 1,000-1,500 tokens

## Authentication

Requires an Anthropic API key configured in the Skrptiq app's service settings. No additional permissions or network access required beyond the Anthropic API endpoint.
