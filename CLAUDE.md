# Second Brain — standing instructions

This is a personal "second brain" note vault. The user **captures raw inputs** into `00-inbox/`.
You (Claude) **read each item, understand it, and write a short clean note** the user can re-read
in 30 seconds and remember the thing. The user never writes notes by hand — they only capture inputs.

## Folder structure

- `00-inbox/` — raw captures, the user's drop zone:
  - `links.md` — URLs, one per line
  - `paste/` — text dumps (copy-paste from Notion, articles, etc.)
  - `images/` — photos of paper notes, screenshots, diagram/Excalidraw exports
- `notes/` — finished clean notes (the output)
- `templates/note-template.md` — the format every note must follow
- `archive/` — processed inbox items go here after they become notes
- `examples/` — sample notes shipped with the template (reference only; never process or move these)
- `CLAUDE.md` — this file

## The "process my inbox" command

When the user says **"process my inbox"**, do this:

1. **Scan** `00-inbox/links.md`, `00-inbox/paste/`, and `00-inbox/images/`.
2. **Announce first.** Before modifying or moving any files, list what you're about to do
   (which items you found, how many notes you'll write, what you'll archive).
3. For **each URL** in `links.md`: fetch it, read it, write a note.
4. For **each text file** in `paste/`: read it, write a note.
5. For **each image** in `images/`: read it (handwriting, screenshot, diagram). For diagrams,
   describe what the diagram shows and its key relationships.
6. **Archive** each processed source into `archive/` so the inbox stays clean.

## How to write a note

- Follow `templates/note-template.md` exactly (frontmatter + the four sections).
- File name: `notes/YYYY-MM-DD-short-slug.md` (today's date, kebab-case slug from the title).
- `type` is one of: `article | tweet | paper-note | diagram | idea`.
- `date` is today's date.
- **Rephrase, never copy-paste.** Summaries are in plain language, in the user's own words.
  The goal is fast recall, not completeness. Keep it SHORT.
- "In one line" = one sentence future-me will understand months later.
- "Key points" = 3–5 plain bullets, only what mattered.
- "Why I saved this" = one line on why it's worth keeping / where it'd be used.
- "Source / raw" = the link, or `scanned from paper {date}`, or the original pasted text.

## Tags & links

- Add **2–5 useful tags** per note.
- If a new note clearly relates to an existing note in `notes/`, add a markdown link between them
  (Obsidian `[[wikilink]]` or standard markdown link).

## Rules of thumb

- The inbox is the user's; `notes/` and `archive/` are yours to maintain.
- Always announce before a batch that moves/modifies many files.
- Never leave a processed source sitting in the inbox — archive it.
- If a single capture clearly covers several distinct topics, it's fine to split it into a few
  short linked notes rather than one long one — fast recall beats one-note-per-file.
- When unsure what an item is, make a reasonable note and pick the closest `type`.
