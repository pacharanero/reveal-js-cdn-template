# Reveal.js CDN Template

A single-file Reveal.js template that loads everything from a CDN. Edit `index.html` and you are done.

## Quick start

1. Open `index.html` and replace the title and content.
2. Keep the CDN links, or pin a version by inserting `@x.y.z` after `reveal.js`.
   - Example: `https://cdn.jsdelivr.net/npm/reveal.js@5.0.4/dist/reveal.css`

## Updating Reveal.js

Pin a CDN version by adding `@x.y.z` to the URLs. To update, change the version number.

Example:

```
https://cdn.jsdelivr.net/npm/reveal.js@5.0.4/dist/reveal.css
```

## Local helper scripts

- `s/serve` runs a local web server using `live-server`.
  - Installs `live-server` globally with `npm` if it is missing.
- `s/pdf` exports `slides.pdf` using DeckTape.
  - Requires Docker to be installed and runnable as a non-root user.

## Notes

- Speaker notes are included in `index.html`. Press `S` to open the speaker view.
- The demo deck showcases fragments, background transitions, auto-animate, and code highlighting.
