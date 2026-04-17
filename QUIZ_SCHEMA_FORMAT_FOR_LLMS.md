# Quiz Schema Format For Other LLMs

Use this file when asking another LLM to generate a quiz schema for this project.

The goal is to produce a schema that works cleanly with this site’s quiz system and is easy to turn into a GitHub Pages quiz page.

## Output Rules

- Return valid JSON only.
- Save it in a `.txt` file if needed, but the contents must still be valid JSON.
- Do not include markdown fences.
- Use UTF-8 friendly plain text.
- Every question must be multiple choice with exactly 4 choices.
- Every question must have exactly 1 correct answer.
- Use 0-based indexing for the correct answer.
- Keep field names exactly as written below.

## Preferred Canonical Format

This is the preferred schema shape for this project.

```json
{
  "schema_version": "1.0",
  "schema_type": "quiz_data",
  "format_note": "Valid JSON stored in a text file for Codex-compatible quiz generation.",
  "quiz_title": "Course or Topic Title - 50-Item Quiz",
  "source_file": "source-material.pdf",
  "question_type": "multiple_choice_single_answer",
  "total_questions": 50,
  "shuffle_questions": false,
  "shuffle_choices": false,
  "passing_score_percent": 70,
  "instructions": [
    "Read each question carefully.",
    "Choose one best answer.",
    "Use the correct_choice_index field for scoring."
  ],
  "rendering_hints_for_codex": {
    "layout": "full_list",
    "show_score_after_submit": true,
    "show_correct_answers_after_submit": true,
    "show_explanations_after_submit": true,
    "progress_bar": true,
    "allow_retry": true
  },
  "questions": [
    {
      "id": 1,
      "topic": "Topic Name",
      "source_pages": [4, 5],
      "question": "Question text goes here?",
      "choices": [
        "Choice A",
        "Choice B",
        "Choice C",
        "Choice D"
      ],
      "correct_choice_index": 2,
      "explanation": "Short explanation of why the answer is correct."
    }
  ]
}
```

## Required Top-Level Fields

- `schema_version`
  - String.
  - Use `"1.0"`.

- `schema_type`
  - String.
  - Use `"quiz_data"`.

- `quiz_title`
  - String.
  - Human-readable title shown on the quiz page.

- `source_file`
  - String.
  - Name of the source deck, PDF, notes file, or lecture file.

- `question_type`
  - String.
  - Use `"multiple_choice_single_answer"`.

- `total_questions`
  - Number.
  - Must exactly match the number of objects in `questions`.

- `shuffle_questions`
  - Boolean.

- `shuffle_choices`
  - Boolean.

- `passing_score_percent`
  - Number.
  - Usually `70`.

- `instructions`
  - Array of strings.

- `rendering_hints_for_codex`
  - Object.

- `questions`
  - Array of question objects.

## Required Fields Per Question

- `id`
  - Number or integer-like value.
  - Must be unique.
  - Recommended: sequential `1, 2, 3...`

- `topic`
  - String.
  - Used for quiz filtering.

- `source_pages`
  - Array of page numbers.
  - If exact pages are unknown, use an empty array `[]`.

- `question`
  - String.

- `choices`
  - Array of exactly 4 strings.

- `correct_choice_index`
  - Number.
  - Must be one of `0`, `1`, `2`, or `3`.

- `explanation`
  - String.
  - Short, direct, and tied to the source.

## Content Quality Rules

- Questions must be answerable from the provided material.
- Avoid duplicate questions.
- Avoid trick wording unless the source specifically teaches distinctions.
- Keep distractors plausible but clearly wrong.
- Explanations should be concise and useful.
- Topics should be consistent and reusable as filter labels.
- If the quiz mixes question styles, still keep the same structural format.

## Strong Recommendations

- Prefer `questions` over `items`.
- Prefer `correct_choice_index` over `answer`.
- Prefer `source_file` and `source_pages` for traceability.
- Include `explanation` for every item.
- Keep punctuation normal and avoid broken encoding characters.

## Optional Fields

These are allowed but not required:

- `format_note`
- `difficulty`
- `estimated_time_minutes`
- `course_code`
- `unit_title`
- `tags`

If optional fields are included, do not remove or rename the required fields.

## Validation Checklist

Before giving the schema back, verify:

1. The JSON parses correctly.
2. `total_questions` equals the actual number of questions.
3. Every question has exactly 4 choices.
4. Every `correct_choice_index` is between `0` and `3`.
5. Every question has a `topic`.
6. Every question has an `explanation`.
7. No trailing commas are present.

## Copy-Paste Prompt For Other LLMs

Use this exact prompt pattern:

```text
Create a quiz schema for my static quiz system.

Requirements:
- Output valid JSON only.
- Do not use markdown fences.
- Follow this exact schema shape:
  - schema_version: "1.0"
  - schema_type: "quiz_data"
  - quiz_title: string
  - source_file: string
  - question_type: "multiple_choice_single_answer"
  - total_questions: number
  - shuffle_questions: boolean
  - shuffle_choices: boolean
  - passing_score_percent: number
  - instructions: string[]
  - rendering_hints_for_codex: object
  - questions: array
- Each question must contain:
  - id
  - topic
  - source_pages
  - question
  - choices (exactly 4)
  - correct_choice_index (0-based)
  - explanation
- Keep the JSON clean and parseable.
- Make sure total_questions matches the number of questions exactly.

Topic/source material:
[paste your lesson, slides, notes, or PDF summary here]
```

## Compatibility Note

This project currently has quiz pages that can work with more than one schema style, but this canonical format is the one to prefer going forward because it is the cleanest, most traceable, and easiest to validate.
