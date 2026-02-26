# Reveal.js CDN Template Agent Guide

This file describes how an agent should create a new presentation from this template. Follow these steps exactly unless the user asks for a different workflow.

## Goal

Create a new presentation by copying this template, then customizing the new `index.html` based on user answers.

## Questions to ask the user (in order)

1. Presentation title
2. Subtitle or tagline (optional)
3. Presenter name and role (optional)
4. Event name and date (optional)
5. Short link or URL for the slides (optional)
6. Theme preference (default: `black`)
7. Any must-have sections or key slides

If the user does not answer an optional question, leave the related content out or keep the template placeholder minimal.

## Steps

1. Choose a destination folder name.
   - Use a date-prefixed slug if the user does not provide one, for example `2026-my-talk-title`.
2. Copy the template folder to the new destination.
   - Copy everything, including `index.html`, `README.md`, `AGENTS.md`, and `s/` scripts.
3. Update `index.html` in the new folder:
   - Replace the `<title>` tag with the presentation title.
   - Update the title slide to include title, subtitle/tagline, presenter, and date if provided.
   - Add the slides URL or short link if provided.
   - Remove demo slides the user does not want.
   - Keep the CDN links unless the user explicitly asks for local assets.
   - Keep the separator regexes exactly as-is unless the user requests changes.
4. Update `README.md` in the new folder:
   - Replace any template references with the new presentation title.
   - Add the slides URL or short link if provided.
5. Confirm the result with the user and list what was changed.

## Implementation hints

- Prefer editing only the new folder after copying.
- Avoid changing the original template unless the user requests it.
- Use clear, minimal slides to start. The demo slides can be removed entirely if the user wants a clean deck.

## Example copy command

```sh
cp -R revealjs-cdn-template 2026-my-talk-title
```

## Example placeholders to replace

- `<title>Reveal.js CDN Template</title>`
- `# Reveal.js CDN Template`
- `### A single-file starter deck`

## Offline conversion command

Use this command phrase when a human wants a fully offline deck:

`convert this presentation to offline reveal.js mode`

When this command is given, do the following in the target presentation repo:

1. Add Reveal.js as a local git submodule:
   - `git submodule add https://github.com/hakimel/reveal.js.git reveal.js`
2. Replace CDN links in `index.html` with local paths:
   - `https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.css` -> `reveal.js/dist/reveal.css`
   - `https://cdn.jsdelivr.net/npm/reveal.js/dist/theme/<theme>.css` -> `reveal.js/dist/theme/<theme>.css`
   - `https://cdn.jsdelivr.net/npm/reveal.js/dist/reveal.js` -> `reveal.js/dist/reveal.js`
   - `https://cdn.jsdelivr.net/npm/reveal.js/plugin/markdown/markdown.js` -> `reveal.js/plugin/markdown/markdown.js`
   - `https://cdn.jsdelivr.net/npm/reveal.js/plugin/highlight/highlight.js` -> `reveal.js/plugin/highlight/highlight.js`
   - `https://cdn.jsdelivr.net/npm/reveal.js/plugin/notes/notes.js` -> `reveal.js/plugin/notes/notes.js`
3. Keep `Reveal.initialize({ hash: true, ... })` and existing plugin config.
4. Keep `s/serve` and `s/pdf` scripts; they should continue to work with local assets.
5. Update `README.md` to state the deck now uses local Reveal.js via submodule for offline presenting.
6. Verify by disconnecting network (or simulating offline) and confirming slides load with styles and navigation intact.

Notes:
- Do not remove markdown separators or presentation content during this conversion.
- If the repository already has a `reveal.js` submodule, reuse it and only fix references as needed.
