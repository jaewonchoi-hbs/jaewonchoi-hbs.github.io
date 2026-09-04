# How to update this site

Everything here can be done from your browser on GitHub — you don't need to
install anything. Find the file, click the pencil icon (**Edit this file**),
make your change, and click **Commit changes**. The live site rebuilds itself
about two minutes later at <https://jaewonchoi-hbs.github.io>.

If a change doesn't show up, go to the **Actions** tab of this repository. A
green check means it deployed; a red X means something in the file you edited
has a formatting problem (usually indentation — see "A note on indentation" at
the bottom).

---

## Add a working paper or publication

Edit **`data/papers.yaml`**. Copy an existing block and change the values.
Keep the two-space indentation exactly as shown.

```yaml
- title: "Your Paper Title"
  authors:
    - "Jaewon Choi"
    - "Coauthor Name"
  year: 2027
  status: "working paper"
  venue: ""
  pdf: "files/paper-slug.pdf"
  link: ""
  job_market_paper: false
  abstract: >-
    One paragraph. Keep every line of the abstract indented four spaces,
    like this, and the whole thing will be treated as a single paragraph.
  presentations:
    - "Conference Name, City, 2027"
```

What the fields do:

| Field | What to put |
|---|---|
| `status` | `working paper`, `work in progress`, `under review`, `revise and resubmit`, `accepted`, or `published` |
| `venue` | The journal name — only once it's accepted or published |
| `pdf` | Path to a PDF you uploaded, e.g. `files/my-paper.pdf`. Leave as `""` for none |
| `link` | An external link instead (SSRN, DOI, publisher page) |
| `job_market_paper` | `true` for your job market paper, `false` otherwise |
| `presentations` | Conferences where you presented it. Delete the field if none |

Papers with status `accepted` or `published` appear under **Publications**;
everything else appears under **Working papers**.

### Attach a PDF to a paper

1. Go to the **`static/files/`** folder in this repository.
2. Click **Add file → Upload files** and drop the PDF in. Use a simple
   lowercase name with no spaces, like `insider-trading-policy.pdf`.
3. In `data/papers.yaml`, set that paper's `pdf` to `"files/insider-trading-policy.pdf"`.

The paper's title on the site then becomes a link to the PDF.

### Mark a paper as published

Change its `status` to `"published"` and fill in `venue`:

```yaml
  status: "published"
  venue: "Journal of Accounting and Economics"
```

### Designate your job market paper

Set `job_market_paper: true` on that one paper. It moves to the top of the
Research section in a highlighted box with its full abstract shown.

---

## Update your bio

Edit **`content/_index.md`**. Everything below the `---` line is your bio —
plain paragraphs, separated by a blank line. Leave the part between the
`---` lines alone.

## Change your tagline, title, or email

Edit **`hugo.yaml`**. The lines you'll most likely want:

```yaml
  role: "PhD Student, Accounting and Management"
  institution: "Harvard Business School"
  email: "jachoi@hbs.edu"
  office: "Wyss Hall 202F, 20 N Harvard Street, Boston, MA 02163"
  tagline: "I am interested in managerial accounting research, ..."
```

Also in `hugo.yaml`, `interests:` is the list of tags shown under your bio, and
`social:` is the list of links (LinkedIn, Google Scholar, GitHub) shown by your
photo and under Contact.

## Add a teaching entry

Edit **`data/teaching.yaml`**:

```yaml
- course: "Financial Reporting"
  role: "Teaching Fellow"
  institution: "Harvard Business School"
  term: "Spring 2028"
  instructor: "Professor Name"
```

Delete the `instructor:` line if there isn't one. The list is shown in the
order it appears in the file, newest first — so add a new appointment at the
**top**.

## Add a degree, an award, or a news item

- **Education** — `data/education.yaml`. Keep `degree:` to the degree itself
  and put the field of study in `field:` with its label (e.g.
  `Concentration: Accounting`) — the parentheses are added for you, and the
  whole parenthetical stays on one line. Honours or your advisor go in
  `note:`, which accepts Markdown, so `*summa cum laude*` renders in italics.
- **Honors and awards** — `data/awards.yaml`. `name:` and `year:` are all most
  entries need. Add an optional `note:` only when the award's name doesn't
  convey what it is (it also accepts Markdown).
- **News** — `data/news.yaml`. This section is hidden until you add something:

  ```yaml
  - date: 2027-03-15
    text: "Presented at the AAA Annual Meeting."
  ```

  The eight most recent items are shown.

## Add software or a data project

Edit **`data/projects.yaml`**. The **Software** section stays hidden while the
file has no entries.

```yaml
- name: "packagename"
  description: "One sentence on what it does."
  url: "https://github.com/username/packagename"
  language: "R"
```

## Update your CV

Upload the new PDF to **`static/files/`** and name it exactly **`cv.pdf`**,
replacing the old one. Keeping the filename means the CV link in your nav bar
and email signature never breaks.

## Change your photo

Replace **`static/images/photo.jpg`**, keeping that exact filename. Crop it
square first — it's displayed as a circle, so a square photo centered on your
face works best. Around 560×560 pixels is plenty.

## Add a blog post

The site has no blog section yet. If you want one, create a file at
`content/blog/your-post-slug/index.md`:

```markdown
---
title: "Post Title"
date: 2027-03-15
description: "One-sentence summary."
---

Your text here.
```

Then add a Blog item to the `menu:` list in `hugo.yaml`, and ask your
assistant to add the blog templates and the homepage teaser block.

## Remove the footer credit

In `hugo.yaml`, change `credit: true` to `credit: false` under
`params.mysite`. Setting `discovery: false` also removes the invisible
`generator` tag and the structured-data block from the page source.

---

## A note on indentation

The `.yaml` files care about spaces. Two rules keep you out of trouble:

1. **Never use tabs.** Only spaces.
2. **Copy an existing entry** and edit the values rather than typing a new
   entry from scratch. That way the indentation is already right.

Each entry in a list starts with `- ` at the left margin, and its remaining
fields line up two spaces in. If a build fails, the Actions log will name the
file and the line number.

---

## Editing on your own computer instead

Optional. If you'd rather preview changes before they go live:

```bash
git clone https://github.com/jaewonchoi-hbs/jaewonchoi-hbs.github.io.git
cd jaewonchoi-hbs.github.io
hugo server
```

Then open <http://localhost:1313>. It reloads as you save. This needs
[Hugo (extended)](https://gohugo.io/installation/) installed —
`winget install Hugo.Hugo.Extended` on Windows, `brew install hugo` on macOS.
Commit and push when you're happy, and the live site follows.
