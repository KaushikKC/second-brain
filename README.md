# 🧠 Second Brain

**You capture. Claude writes the notes.**

A dead-simple personal knowledge system you run on your own machine with
[Claude Code](https://claude.com/claude-code). You drop raw stuff into an inbox —
links, screenshots, photos of paper notes, copy-pasted text — and say *"process my inbox."*
Claude reads each item, understands it, and writes a short, clean note that future-you can
re-read in **30 seconds** and remember the thing.

No app to host. No account to create. No database. Just folders, Markdown, and a prompt.
If you can install one CLI tool, you can be running this in 20 minutes.

---

## Why this exists

Capturing is easy; *writing good notes is the part everyone skips.* So here you only ever
capture. The note-writing — summarizing, rephrasing in plain language, tagging, linking related
ideas — is the agent's job. Your notes stay short and skimmable because the whole point is fast
recall, not completeness.

Works great as an [Obsidian](https://obsidian.md) vault (the notes are plain Markdown with
`[[wikilinks]]`), but Obsidian is optional — any Markdown editor works.

---

## How it works

```
        YOU                          CLAUDE                        YOU
   ┌───────────┐              ┌──────────────────┐          ┌───────────────┐
   │  drop raw │   ───────▶   │ "process my      │  ──────▶ │  re-read clean │
   │  captures │   into       │   inbox"         │  writes  │  notes anytime │
   │           │   00-inbox/  │ reads → rephrases│  to      │               │
   └───────────┘              │ → tags → links   │  notes/  └───────────────┘
                              │ → archives source│
                              └──────────────────┘
```

1. **Capture** — add a URL, a text file, or an image to `00-inbox/`.
2. **Process** — tell Claude `process my inbox`.
3. **Recall** — a tidy note lands in `notes/`; the raw source moves to `archive/`.

---

## Folder structure

```
.
├── 00-inbox/              ← your drop zone (the only folder you touch)
│   ├── links.md           ← URLs, one per line
│   ├── paste/             ← text dumps (.txt / .md / .rtf)
│   └── images/            ← photos, screenshots, diagram exports
├── notes/                 ← finished clean notes (Claude writes here)
├── archive/               ← processed raw captures (Claude moves them here)
├── templates/
│   └── note-template.md   ← the format every note follows
├── examples/notes/        ← sample notes so you can see the output style
└── CLAUDE.md              ← the agent's standing instructions
```

---

## Setup (≈ 20 minutes)

1. **Install Claude Code** — follow the [official guide](https://docs.claude.com/en/docs/claude-code/overview).
2. **Get this template:**
   ```bash
   git clone https://github.com/<your-username>/second-brain.git
   cd second-brain
   ```
   Or click **"Use this template"** on GitHub to make your own private copy.
3. **Open the folder in Claude Code:**
   ```bash
   claude
   ```
   That's it. `CLAUDE.md` tells the agent everything about how to behave — you don't paste any
   prompt. Just start capturing.

> **Tip:** open the same folder as an [Obsidian](https://obsidian.md) vault to get backlinks,
> graph view, and search over your notes.

---

## Daily use

**Capture anything, anytime:**

| You have… | Drop it into… |
|---|---|
| A URL (tweet, blog, article) | a new line in `00-inbox/links.md` |
| Copy-pasted text (Notion, docs) | a file in `00-inbox/paste/` |
| A photo of paper notes / screenshot / diagram export | a file in `00-inbox/images/` |

**Then, whenever you like, say:**

```
process my inbox
```

Claude will tell you what it found, write a note per item (in plain language, never copy-pasted),
add 2–5 tags, link related notes, and move each raw source into `archive/`. Your inbox goes back
to empty.

Other things you can say: *"process just the links"*, *"process this one image"*,
*"redo that last note shorter"*.

---

## The note format

Every note follows [`templates/note-template.md`](templates/note-template.md):

```markdown
---
title:
source:
date: {today}
tags: []
type: article | tweet | paper-note | diagram | idea
---
# {title}
## In one line
{one sentence you'll understand months later}
## Key points
- {3-5 bullets, plain language, only what mattered, in your own words}
## Why I saved this
{one line: why it's worth keeping / where you'd use it}
## Source / raw
{link, or "scanned from paper {date}", or the original text}
```

See [`examples/notes/`](examples/notes/) for real output (a set of interlinked AI-fundamentals
notes built from pasted study material).

---

## Make it yours

- **Change the note shape** → edit `templates/note-template.md`.
- **Change the agent's behavior** → edit `CLAUDE.md` (tone, tags, when to split notes, languages).
- **Add note types** → tweak the `type:` list in both files.

---

## FAQ

**Does this send my notes anywhere?** Only the inbox items you ask Claude to process are read by
the model during processing. Your notes live as plain files on your machine. Host them wherever
you like (private GitHub repo, iCloud, Syncthing…).

**Do I need Obsidian?** No. Notes are plain Markdown. Obsidian just makes browsing/linking nicer.

**Can I use a different agent/LLM?** The structure is just folders + Markdown + a `CLAUDE.md`
instruction file. Any capable coding agent that can read files and fetch URLs can follow it.

---

## License

[MIT](LICENSE) — do whatever you want, no warranty.

---

*Built with [Claude Code](https://claude.com/claude-code). Contributions and forks welcome.*
