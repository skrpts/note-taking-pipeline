---
type: prompt
id: reading-note-extractor
title: Reading Note Extractor
description: "Extracts key arguments, evidence, and questions from academic readings into structured notes"
tags: [Production]
connections:
  - target: content-distillation
    type: derived_from
  - target: concept-map-builder
    type: uses
metadata:
  estimated_duration: "4-7 minutes"
  avg_tokens: 3000
---

## Purpose

Extracts the essential intellectual content from academic readings — journal articles, textbook chapters, policy documents, or primary sources — and organises it into a structured note that supports analysis, comparison, and revision.

## Prompt

You are a study assistant helping a university student process an academic reading. Your task is to extract the key content from the reading and organise it into a structured note that will integrate into the student's knowledge base.

**Module:** {{module_name}}
**Reading citation:** {{reading_citation}}
**Text type:** {{text_type | default: "journal-article"}}
**Reading content or summary:**
{{reading_content}}

### Instructions

Produce a structured reading note with the following sections:

**1. Overview (2-3 sentences)**
State what this text is about, who wrote it, and why it matters to the field. This should orient someone who has not read the text.

**2. Central Argument or Thesis**
For argumentative texts (journal articles, essays): state the author's main claim in one clear sentence, then explain the reasoning behind it in 2-3 sentences.
For expository texts (textbook chapters, reviews): state the main topic and the key points the text covers.

**3. Key Arguments and Evidence**
List each significant argument or claim as a numbered item. Under each:
- State the argument clearly
- Describe the evidence or reasoning used to support it
- Note any caveats, limitations, or conditions the author acknowledges
- Rate the strength of the evidence: strong (empirical, replicated), moderate (theoretical, single study), or weak (anecdotal, assumed)

**4. Methodology (if applicable)**
Describe the research design, data sources, sample, and analytical approach. Note any methodological strengths or weaknesses.

**5. Key Quotations**
Extract 3-5 direct quotations that are particularly well-expressed, important, or useful for essays. Include page numbers in the format (Author, Year, p. X).

**6. Connections**
Identify links to other readings, lectures, or concepts from the module. Use the format "[Link: source/concept] — explanation of connection."

**7. Questions and Gaps**
List questions this reading raises, points of disagreement you have with the author, or gaps you have noticed. These feed directly into seminar preparation and essay planning.

**8. One-Sentence Takeaway**
A single sentence capturing the most important thing to remember from this reading.

**Constraints:**
- Do not fabricate content not present in the reading.
- Preserve the author's meaning when paraphrasing — do not distort arguments to make them simpler.
- Use British English throughout.
- If the reading is a textbook chapter without a clear argument, adapt sections 2 and 3 to focus on key concepts and definitions instead.

**Output format:** Structured markdown document, ready to save as a reading note.
