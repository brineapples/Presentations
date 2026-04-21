# Presentation Page Format

Use this guide when creating future presentation pages for this project.

This format is based on [manufacturer_system_presentation.html](/c:/Users/nulln/source/repos/Presentations/manufacturer_system_presentation.html).

## Goal

Every presentation page should:

- feel like part of the same site as the hub and quizzes
- stay fully static for GitHub Pages
- preserve the bold slide-deck style already used in the manufacturer presentation
- remain viewable on mobile, not only on desktop

## Core Design Pattern

Follow the manufacturer presentation model:

- one long single-page presentation
- multiple full-screen or near-full-screen sections
- strong hero intro
- section-based storytelling
- decorative glow/grid background
- animated reveal behavior
- visual navigation between sections

## Required Structure

- Strong hero/cover section
- Distinct content sections
- Clear headings and subtitles
- Reusable visual cards and pills
- On-page navigation or slide dots when appropriate
- Consistent typography and accent color treatment

## Mobile Requirement

This is not optional.

The manufacturer presentation should be treated as the standard, but with explicit mobile care:

- do not assume desktop-only viewing
- do not rely on fixed-width layouts that break on phones
- reduce slide padding and font sizes at smaller widths
- stack multi-column sections vertically on smaller screens
- make dense diagrams degrade gracefully instead of overflowing
- move fixed side navigation into a bottom touch-friendly layout on mobile when needed
- disable scroll-snap on small screens if it hurts usability
- test from a mobile viewport whenever possible (Priority)

If a section is diagram-heavy:

- simplify or stack the layout on mobile
- let labels wrap
- avoid unreadably tiny text
- prefer vertical flow over squeezed horizontal compression

## Styling Rules

- Keep the existing site’s visual direction:
  - black / charcoal atmospheric background
  - neutral white/silver accents
  - layered glow effects
  - geometric grid overlays
  - bold, presentation-like typography
- Reuse the same font family patterns where possible.
- Keep transitions polished but not distracting.

## GitHub Pages Rules

- Pure HTML, CSS, and JavaScript only
- Relative links only
- No backend dependencies
- No build step required

## Validation Checklist

Before considering a presentation done:

1. Verify the page loads directly as a static HTML file.
2. Verify section navigation still works.
3. Verify no section causes horizontal scrolling on mobile.
4. Verify hero text fits on narrow screens.
5. Verify dense cards, grids, or diagrams stack properly.
6. Verify mobile view around `390px` width.
7. Verify tap targets are usable on touch devices.

## Recommended Prompt Direction

When asking for a new presentation page, use language like:

`Create a static presentation page using the same design language as manufacturer_system_presentation.html. Keep the long-form slide style, but make mobile view a hard requirement: stacked layouts, readable headings, touch-friendly navigation, and no horizontal overflow at phone widths.`
