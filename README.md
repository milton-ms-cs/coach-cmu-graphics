# cmu-graphics-coach

Codio Custom Assistant ("CMU Graphics Coach") for 7th grade students learning Python with CMU Graphics at Milton Academy.

A single `index.js` + `metadata.json`, no build step. On every question it reads the student's open editor files and the assignment guide. The system prompt embeds a full CMU Graphics reference (shapes, properties, event handlers, groups, collision detection), bridges from micro:bit concepts the students already know, and enforces a strict teach-don't-type policy: direct diagnosis for errors and typos, Socratic guidance for design questions, generic 1-3 line snippets only.

## Development

```bash
node --check index.js
```

See the parent `coaches/CLAUDE.md` for the shared coach architecture and API quirks. Deployment: bump `VERSION` in `index.js`, commit, then run `../publish_coaches.sh --publish` from the parent folder and Check for Updates in Codio. Typing `version` at any coach prompt confirms the release propagated.
