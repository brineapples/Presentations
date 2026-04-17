# Quiz Page Format

Use this guide when adding or generating future quiz pages for this project.

This format is based primarily on [hci_quiz_100_items.html](/c:/Users/nulln/source/repos/Presentations/hci_quiz_100_items.html), which is the main basis for quiz styling, structure, and interaction behavior.

## Goal

Every quiz page should:

- fit the same visual family as the site hub
- work as a static GitHub Pages page
- be mobile-usable, not just desktop-usable
- support score tracking and progress feedback
- keep the quiz readable even when there are many questions

## File Placement

- Put quiz pages at the project root.
- Prefer simple names like `topic_quiz_50_items.html`.
- If a schema file is used, keep it at the project root too.

## Required Quiz Features

- Back link to `index.html`
- Large hero section with:
  - quiz label
  - quiz title
  - short explanation of what the quiz covers
  - quick summary pills
- Scoreboard panel with:
  - answered count
  - correct count
  - accuracy
  - remaining count
  - progress bar
- Filter/action panel
- Full question list rendering
- Per-question answer checking
- Per-question clear button
- Per-question reveal answer button
- Global reset progress button
- Global reveal all answers button

## Preferred Interaction Pattern

Match the HCI quiz pattern:

- render all questions in a long scroll page
- allow instant checking instead of requiring one final submit
- visually mark selected, correct, and incorrect choices
- show the correct answer after an item is answered
- show explanation text when the schema supports it
- support filtered study by topic
- support shuffled question order when useful

## Styling Rules

- Reuse the same visual language:
  - blue-black background
  - cyan accent glow
  - DM Sans / Inter / DM Mono stack
  - glassy bordered cards
  - subtle animated particle/cursor background
- Keep quiz cards rounded and readable.
- Use strong contrast for question text.
- Avoid tiny tap targets.

## Mobile Requirements

This is mandatory.

- Design for narrow phone widths around `390px`.
- Buttons and selects should be at least comfortable for touch.
- Filter grids must collapse to one column on mobile.
- Score grids must collapse cleanly.
- Long topic labels must wrap instead of overflow.
- Question cards must remain readable without horizontal scrolling.
- Hero titles must be reduced for phones so they do not clip.

## Data Expectations

Quiz pages may be built in either of these two ways:

1. Embedded schema data inside the HTML
2. External schema loaded with `fetch()`

Preferred going forward:

- external schema file when GitHub Pages delivery is expected
- embedded data only when reliability or portability is more important

## Compatible Question Schema Concepts

A quiz page should be able to work with fields such as:

- `id`
- `topic`
- `question`
- `choices`
- `correct_choice_index`
- `answer`
- `explanation`
- `source_pages`
- optional type metadata

If the schema uses a different shape, normalize it in JavaScript before rendering.

## Validation Checklist

Before considering a quiz page done:

1. Verify the file loads from the correct GitHub Pages path.
2. Verify the page renders with JavaScript enabled.
3. Verify at least one answer can be selected and scored.
4. Verify `Reset Progress` works.
5. Verify `Reveal All Answers` works.
6. Verify filtering works without breaking the score display.
7. Verify the page at about `390px` width.
8. Verify there is no horizontal overflow.

## Recommended Prompt Direction

When asking for a new quiz page, use language like:

`Make a static GitHub Pages quiz page using the same style and interaction model as hci_quiz_100_items.html. Keep it mobile-friendly, include live scoring, progress tracking, reset, reveal-all, and topic filtering when possible.`
