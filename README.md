# jaewonchoi-hbs.github.io

Personal academic website for Jaewon Choi, PhD student in Accounting and
Management at Harvard Business School.

**Live at <https://jaewonchoi-hbs.github.io>**

## How it works

A [Hugo](https://gohugo.io) static site with custom layouts and one
stylesheet — no theme framework, no JavaScript framework, no build tooling
beyond Hugo itself. Pushing to `main` triggers
[`.github/workflows/deploy.yml`](.github/workflows/deploy.yml), which builds
the site and publishes it to GitHub Pages in about two minutes.

## Where things live

| Path | What's in it |
|---|---|
| `hugo.yaml` | Name, title, email, tagline, research interests, social links, nav menu |
| `content/_index.md` | The homepage bio |
| `data/papers.yaml` | Working papers and publications |
| `data/teaching.yaml` | Teaching history |
| `data/education.yaml` | Degrees |
| `data/awards.yaml` | Honors and awards |
| `data/projects.yaml` | Software and data projects (section hidden while empty) |
| `data/news.yaml` | Recent updates (section hidden while empty) |
| `static/files/cv.pdf` | The CV linked from the nav bar |
| `static/images/photo.jpg` | Headshot |
| `assets/css/style.css` | All styles |
| `layouts/` | Templates — `index.html` is the homepage |

## Making changes

See **[UPDATING.md](UPDATING.md)** — a plain-language guide to adding a paper,
updating the bio, replacing the CV, and everything else, written for editing
files directly on GitHub.

## Local preview

Requires [Hugo extended](https://gohugo.io/installation/).

```bash
hugo server
```

Then open <http://localhost:1313>.

## First-time GitHub Pages setup

In this repository: **Settings → Pages → Build and deployment → Source:
GitHub Actions**. Only needed once.
