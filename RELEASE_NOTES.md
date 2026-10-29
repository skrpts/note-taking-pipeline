# Release Notes

## v1.1.30
GH#1100 retrospective repair — the data flowed backwards.

`take-notes`'s slot is labelled **"Prior Analysis"** and was bound to Spaced Repetition Design, whose output is the flashcards. Flashcards are generated FROM notes, so the note-taking stage was receiving a derivative of its own product. Re-bound to Knowledge Linking, whose concept map is the prior analysis the label asks for.

## v1.1.29
GH#1045 — wire the `reading-note-extractor` prompt into the pipeline so Stage 2 actually runs. It shipped declared but uninvoked, so a package whose own documentation promises a Reading Extraction stage — "pulls out the key arguments, supporting evidence, author position and terminology" — never produced any of it, and knowledge linking and weekly synthesis consumed notes that had no reading extraction in them.

Added a `reading-extraction` backing skill rather than a second entry on `content-distillation`, which Stage 2's prose names but Stage 1 already occupies: two entries on one skill slug share its title, so every `from_step` naming it resolves to one of them silently. The step is the entry point for the reading strand and has no upstream producer, so its content is a declared `context_param` bound `from_input` from a new `reading_content` workflow input — the same shape GH#1124's fix used for its position-1 step, and nothing is bound that the step does not genuinely consume. Skills 3→4, total 12→13.

## v1.1.28
GH#1100 consumer wave (batch 2) — declare the data flow this workflow was resolving positionally.

Each stage below now receives its input through a declared `bindings:` entry instead of `default_from_previous`, which K-073 revoked. **The value is unchanged**: every binding names the step that immediately precedes it, which is exactly what the positional default resolved to. What changes is that the dependency is stated rather than inferred from position, so a reorder can no longer silently feed a stage the wrong artefact.

Bindings added:
  `take-notes` ← `from_step: "Spaced Repetition Design"` (step 4)
  `polish-language` ← `from_step: "Weekly Synthesis Template"` (step 7)

Dependency pins moved to the published versions that declare these slots:
  `cornell-notes-template` 1.0.1 → 1.0.2
  `polish-language` 1.0.1 → 1.0.7
  `take-notes` 1.0.3 → 1.0.4

## v1.1.27
GH#1044 — document the inputs this workflow's prompts REQUIRE but its Inputs table never listed. A user supplying exactly what the table asked for was running with required parameters unsatisfied — a silent wrong run, not a documentation nicety. documented 1 input(s): study_material. Every row is generated from the requiring prompt's own declared description, example and required flag — none invented. No behaviour change; documentation only.

## v1.1.26
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.25
GH#745 — declare per-step `output: {name, type}` on every execution step (structured_notes/text, concept_map/text, flashcards/list, notes/text, cornell_notes/text, weekly_synthesis/text, polished_notes/text). Lights up the #744 rich flow-map. Content-only; no bindings or logic changes.

## v1.1.24
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 6 inline shared-content files and declare 6 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.23
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.22
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.21
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.20
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.19
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
