# KharmaLab website

The source files for **https://kharmalab.cloud**.

This is a plain static website — no build step, no database, no server. The site is just five files: four HTML pages and one `CNAME` file. GitHub serves them; the domain `kharmalab.cloud` points at GitHub via DNS.

---

## File overview

```
index.html         → the home / about page (this is what visitors see first)
publications.html  → publication list, grouped by year
projects.html      → active and recent research projects
people.html        → PI bio + team members + alumni
CNAME              → tells GitHub which custom domain to serve from
README.md          → this file
```

Each HTML file is self-contained: it includes the styling, fonts, and navigation menu inline. Editing one page does not affect the others.

---

## How to edit a page

You need nothing more than a plain text editor (Notepad on Windows, TextEdit on macOS, or any code editor like VS Code).

1. Open the `.html` file you want to change.
2. **Read the comment block at the top of the file.** Each page begins with a comment explaining its structure and how to edit it.
3. Find the section you want to change (use Find / Ctrl-F).
4. Edit the visible text. Do **not** edit the tags themselves (the things in angle brackets like `<h1>` and `</p>`).
5. Save the file.
6. Commit the change to the `main` branch on GitHub (either through the GitHub web UI or via Git).
7. Wait 1–2 minutes. The site updates automatically.

### Worked examples already in the files

To make it obvious what filled-in content should look like, each page has at least one fully written-out example:

- `index.html` — research areas and the latest publication line.
- `publications.html` — the 2026 paper at the top.
- `projects.html` — the first project card (the inverse folding EA framework).
- `people.html` — the PI card and the first member card.

Everything else on those pages is `[PLACEHOLDER]` text in brackets. Replace each bracketed phrase with the real content.

---

## Adding a new entry

### A new publication

Open `publications.html`, find the right year section, copy the `<article>...</article>` block from any existing entry, paste it directly below, and replace the four fields: title, authors, venue, links.

### A new project

Open `projects.html`, copy any `<article>...</article>` block, and replace the title, description, status, lead, and links.

### A new team member

Open `people.html`, copy any `<article>...</article>` block in the "Current members" section, and replace the name, role, years, bio, and links. To add a real photo, see the instructions in the comment at the top of `people.html`.

---

## Adding photos

There is no photos folder yet. To add member photos:

1. Create a folder called `photos/` in this repository.
2. Add image files (JPEG or PNG), one per person, named like `firstname-lastname.jpg`.
3. In `people.html`, replace the placeholder grey circle `<div class="...rounded-full bg-line..."></div>` with an `<img>` tag — the comment block at the top of `people.html` shows the exact syntax.

Recommended photo dimensions: square, at least 200×200 pixels. JPEG compressed to under 200 KB each.

---

## Animation on the home page

The small DNA → RNA animation on the home page is pure SVG. It loops every 10 seconds. To change it:

- **Slow it down**: search `index.html` for `dur="10s"` and change `10s` to a larger number (e.g. `15s`) everywhere it appears.
- **Change colors**: search for `stroke="#a5a5a0"` and `fill="#6e6e6c"` and replace with your colors.
- **Remove it entirely**: delete the entire `<svg>...</svg>` block in the hero section. The page layout will adjust automatically.

---

## Deployment

The site is hosted on GitHub Pages. Every push to the `main` branch triggers a redeployment, which takes about one minute.

### DNS setup (already done — for reference only)

The domain `kharmalab.cloud` is configured at the domain registrar with these records:

```
Type   Host    Value
A      @       185.199.108.153
A      @       185.199.109.153
A      @       185.199.110.153
A      @       185.199.111.153
CNAME  www     KharmaLab.github.io
```

In the GitHub repository: **Settings → Pages → Custom domain** is set to `kharmalab.cloud`, and **Enforce HTTPS** is enabled.

If the domain ever stops working, this is the first thing to check.

---

## Fonts and styling

The site uses two fonts loaded from Google Fonts:

- **Fraunces** (serif) — for headings and the lab name.
- **IBM Plex Sans** (sans-serif) — for body text and navigation.

Both are free and open-source. They are loaded via `<link>` tags at the top of each HTML file.

The color palette is intentionally monochrome (off-white background, dark grey text, faint grey for accents). To change the palette, edit the `colors:` block in the `<script>` tag at the top of any HTML file. The same five colors are used everywhere:

```
ink    → main text                        (#1a1a1a — near-black)
paper  → page background                  (#fafaf7 — off-white)
muted  → secondary text                   (#6e6e6c — medium grey)
faint  → tertiary text, dividers          (#a5a5a0 — light grey)
line   → horizontal rules, avatar bg      (#e5e5e0 — very light grey)
```

---

## Questions

For technical issues, open an issue on this repository.
