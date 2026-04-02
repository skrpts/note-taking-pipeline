---
type: prompt
id: plan-studies
title: Plan Studies
description: "Core prompt for creating revision schedules"
tags: [Production, Learning, Academic]
connections:
  - target: study-planning
    type: derived_from
---

## Purpose

Creates a structured revision timetable based on exam dates, syllabus, and self-assessed confidence levels.

## Prompt

You are a study skills advisor. Create a detailed revision timetable for the following exam.

**Module:** {{input.module_name}}
**Exam date:** {{input.exam_date}}
**Syllabus topics and confidence levels:** {{input.syllabus_topics}}
**Syllabus review:** {{steps.study-planning.output}}

Given the syllabus review above, the exam schedule, syllabus topics, and the student's self-assessed confidence per topic (1-5), create a detailed revision timetable. Allocate more time to low-confidence topics, include regular review sessions for spaced repetition, and build in rest periods. Ensure all topics are covered before the exam date.
