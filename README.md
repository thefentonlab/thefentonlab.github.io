# The Fenton Lab website

A static site built with Jekyll and hosted free on GitHub Pages.
You do not need to install anything or use a terminal. Everything below
happens in a web browser on github.com.

---

## Getting it online (one time, about 20 minutes)

1. Make a free account at github.com.
2. Click **New repository**. Name it `fentonlab`. Set it to **Public**. Create it.
3. On the new repo page, click **uploading an existing file**. Drag in
   everything from this folder. Scroll down and click **Commit changes**.
4. Go to **Settings** → **Pages**. Under "Build and deployment", set
   Source to **Deploy from a branch**, branch to **main**, folder to **/ (root)**.
   Save.
5. Wait two minutes, then reload. GitHub shows you the live URL.

### Pointing thefentonlab.com at it

1. Transfer the domain out of Wix to a registrar such as Cloudflare or
   Namecheap. Do this **before** cancelling anything at Wix. Allow two weeks.
2. At the registrar, add these DNS records:

   | Type  | Name | Value |
   |-------|------|-------|
   | A     | @    | 185.199.108.153 |
   | A     | @    | 185.199.109.153 |
   | A     | @    | 185.199.110.153 |
   | A     | @    | 185.199.111.153 |
   | CNAME | www  | YOURUSERNAME.github.io |

3. Back in **Settings → Pages**, enter `thefentonlab.com` under Custom domain.
4. Tick **Enforce HTTPS** once it becomes available (can take an hour).

---

## Everyday editing

All of this is done on github.com: open the file, click the pencil icon,
edit, scroll down, click **Commit changes**. The site rebuilds in about a minute.

### Add a publication

Open `_data/publications.yml`. Add a new block **at the top**:

```yaml
- number: 3
  cite: >
    Author, A.; Fenton, J. L. Title of the Paper.
    <em>J. Am. Chem. Soc.</em> <strong>2026</strong>, <em>148</em>, 1234–1240.
  doi: https://doi.org/10.1000/whatever
  image: toc/mypaper.png
  note: Invited perspective
```

- `number` — highest is newest. Just use the next one up. Nothing else changes.
- `cite` — HTML works: `<em>italic</em>`, `<strong>bold</strong>`, `<sub>2</sub>`
- `image` and `note` are optional. Leave the lines out entirely if not needed.
- TOC graphics go in `assets/img/toc/`, exported around 800px wide.

### Add a person

Open `_data/people.yml` and copy one of the existing blocks.
Photos go in `assets/img/people/`. Crop them all to 4:5 portrait
(graduate students) or 1:1 square (undergraduates) before uploading.

To move someone to alumni, cut their block out of `graduate:`
and add a line under `alumni:`.

### Add news

Open `_data/news.yml`. New entries go at the top. The `date` is free
text, so "September 2026" or "Fall 2026" both work.

### Edit page text

- Homepage: `index.html`
- Research: `research.md`
- Join: `join.md`

`.md` files are Markdown: `#` is a heading, `##` a subheading, blank lines
separate paragraphs, `[text](url)` is a link.

### Upload an image

Navigate to `assets/img/` on github.com, click **Add file** →
**Upload files**, drag it in, commit. Then reference it by filename.

---

## Changing the design

Everything visual is in `assets/css/style.css`. The top of that file
has a block called `:root` with every color, the content width, and the
section padding. Change a value there and it changes across the whole site.

```css
--accent: #1E407C;   /* links and buttons */
--wrap:   1200px;    /* content column width */
--pad:    84px;      /* space above and below each section */
```

Fonts are loaded in `_layouts/default.html` from Google Fonts, and set in
the `body` and `h1,h2,h3` rules in the stylesheet.

The header and footer live in `_includes/`. Editing them changes every page.

---

## Images still needed

Replace these placeholders with real files of the same name:

- `assets/img/hero.jpg` — 2400px wide, dark and dense
- `assets/img/research-1.jpg`, `-2`, `-3` — 4:3
- `assets/img/people/julie.jpg` and one per student — 4:5

---

## If something breaks

The site is in version control, so nothing is ever lost. On github.com
click the **commits** link (the clock icon above the file list), find the
version from before the problem, and revert to it.

A page that goes blank after an edit to a `.yml` file is almost always an
indentation error. YAML cares about spaces. Compare your new block against
one that already works.
