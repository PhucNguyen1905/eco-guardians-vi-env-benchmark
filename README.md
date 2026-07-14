# Eco Guardians — Vietnamese Environmental Dialogue Benchmark (480 items)

A 480-item Vietnamese-language benchmark for evaluating child-oriented NPC dialogue in environmental learning games, released with the ISCSET 2026 paper:

> Phuc Nguyen and Chau Vo, *"Eco Guardians: A Vietnamese Environmental Learning Game Prototype Using LLM-Driven Educational Non-Player Characters,"* in Proc. 15th International Symposium on Computer Science and Educational Technology (ISCSET), IEEE, 2026 (to appear).

## Overview

The benchmark supports controlled comparison of LLM candidates for child-facing (ages 8–12) Vietnamese environmental education dialogue across contexts, question formats, difficulty levels, and Knowledge–Attitude–Behavior (KAB) labels. It is a controlled evaluation set — not logs of real child dialogue — so models can be tested on identical prompts without exposing child-participant data.

| Dimension  | Breakdown |
|------------|-----------|
| Total      | 480 Vietnamese questions |
| Type       | 320 multiple-choice (MCQ); 160 short answer (SA) |
| Context    | `CITY`, `FOREST`, `OCEAN`, `GENERAL` — 120 each (80 MCQ + 40 SA) |
| Difficulty | Easy 192; Medium 180; Hard 108 |
| KAB label  | Knowledge 308; Behavior 110; Attitude 62 |

## Data format

`data/benchmark_480.json` — a JSON array of 480 items:

```json
{
  "id": "CITY_MCQ_1",
  "map": "CITY",
  "concept": "Ô nhiễm không khí",
  "difficulty": "Easy",
  "type": "MCQ",
  "k_type": "Knowledge",
  "question_text": "Những hoạt động nào ở thành phố thường gây ô nhiễm không khí?",
  "options": ["...", "...", "...", "..."],
  "correct_answer": "C",
  "explanation": "..."
}
```

Short-answer (`"type": "SA"`) items have no `options`/`correct_answer`; the `explanation` field serves as the reference answer.

## Construction and quality assurance

- Items were generated through a controlled LLM-assisted protocol grounded in a documented reference corpus of 18 source files (Vietnamese primary-school environmental education teaching materials, UNEP guidance, NASA Climate Kids, US EPA student activities).
- The generation model (Claude Opus 4.5, Anthropic) is intentionally from a different model family than all candidate models (Llama, Gemini, Phi) and judge models (GPT-4o-mini, Gemini 3 Flash Preview, GPT-5) used in the paper's evaluation, to reduce same-family stylistic bias.
- Quality assessment: 3 LLM judges + 9 independent human evaluators scored all 480 items on an 11-point rubric (exemplar threshold ≥ 9). Both sources classified all items as exemplar; this is threshold acceptance, not proof of uniformly perfect item quality (LLM judges' weakest MCQ dimension was distractor quality, 65.8% full-score rate; human single-rater agreement was limited — mean pairwise Pearson r = 0.326, ICC(single) = 0.314 — while the 9-rater average was stable, ICC(average) = 0.805).
- The dataset is quality-assessed for controlled model comparison. It is **not** psychometrically validated as a classroom assessment.

## Intended use and limitations

- Intended: benchmarking LLM dialogue quality (factuality, age fit, Vietnamese pronoun consistency, structured-output reliability, latency) for child-oriented environmental education NPCs.
- Not intended: classroom assessment of children, training data for child-facing systems without further validation, or safety certification of any kind.

## Citation

```bibtex
@inproceedings{nguyen2026ecoguardians,
  author    = {Nguyen, Phuc and Vo, Chau},
  title     = {Eco Guardians: A Vietnamese Environmental Learning Game Prototype Using LLM-Driven Educational Non-Player Characters},
  booktitle = {Proc. 15th International Symposium on Computer Science and Educational Technology (ISCSET)},
  publisher = {IEEE},
  year      = {2026},
  note      = {to appear}
}
```

## License

Released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). See `LICENSE`.
