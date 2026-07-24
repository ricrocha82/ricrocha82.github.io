# ricrocha82.github.io

Personal website for **Ricardo R. Pavan** — bioinformatics scientist, working on reproducible
computational methods for microbiome, virome, and biomedical research. Built with
[Quarto](https://quarto.org), deployed to GitHub Pages.

## Why Quarto

The site needs to support Python and R tutorials with executable code, statistical/data
visualization posts, citations, equations, and syntax highlighting, while staying
maintainable by someone who works primarily in Python, R, Markdown, and Git — with no
database, no JS framework, and minimal build complexity. Quarto satisfies all of this
natively (see the audit/comparison shared before this build for the full reasoning).

## Directory structure

```
.
├── _quarto.yml              # site config: nav, theme, SEO metadata
├── _variables.yml           # SINGLE SOURCE OF TRUTH: name, email, links, positioning statement
├── index.qmd                 # Homepage
├── about/index.qmd           # About page (career narrative)
├── projects/                 # One .qmd per project (see "Add a project" below)
│   ├── index.qmd              # auto-generated listing (Quarto `listing`)
│   └── _template.qmd          # copy this to add a new project
├── publications/
│   ├── index.qmd              # auto-generated, filterable listing
│   ├── references.bib         # BibTeX — canonical citation data
│   ├── apa.csl                # citation style
│   └── _template.qmd          # copy this to add a new publication
├── software/
│   └── index.qmd              # CRESSENT + other software entries
├── tutorials/
│   ├── index.qmd              # blog-style listing
│   └── posts/<slug>/index.qmd # one folder per tutorial
├── data-stats/
│   ├── index.qmd
│   └── posts/<slug>/index.qmd
├── cv/index.qmd              # web CV summary + PDF download buttons
├── contact/index.qmd
├── 404.qmd
├── files/cv/                  # <- put your CV/résumé PDFs here (see below)
├── images/                    # profile photo, project/software placeholder images
├── styles/                    # theme-light.scss, theme-dark.scss, custom.css, head-meta.html
└── .github/workflows/publish.yml   # build + deploy to GitHub Pages
```

## Local installation

1. Install [Quarto](https://quarto.org/docs/get-started/) (CLI ≥ 1.6).
2. Install Python + packages used by the one executable tutorial demo:
   ```
   pip install jupyter matplotlib scikit-learn pandas numpy
   ```
3. (Only if/when you add R-based tutorials) install R + `rmarkdown`, `knitr`, `tidyverse`.

## Local preview

```
quarto preview
```
This opens a live-reloading local server. Edits to `.qmd` files refresh automatically.

## Full build

```
quarto render
```
Output goes to `_site/` (git-ignored — this is what gets deployed, not committed to `main`).

## How to update things

### Update your name, links, email, or positioning statement
Edit **`_variables.yml`** only. Every page references these via `{{< var key >}}` —
one edit updates the whole site.

### Add a project
1. Copy `projects/_template.qmd` → `projects/your-project-slug.qmd`
2. Fill in the front matter (`title`, `date`, `image`, `categories`, `status`) and the
   13-section body (Overview, Problem, Role, Data, Methods, Workflow, Results, Challenges,
   Publications, Code, Collaborators, Status, Limitations).
3. Add a placeholder or real image to `images/projects/`.
4. It will appear automatically on `/projects` and can be added to the homepage's
   "Featured projects" grid by editing `index.qmd` directly.

### Add a tutorial or data/statistics post
1. Copy `tutorials/posts/_template/` (or `data-stats/posts/_template/`) to a new folder,
   e.g. `tutorials/posts/my-new-tutorial/`.
2. Edit `index.qmd` inside it — front matter (`title`, `date`, `categories`, `draft`) and
   the 12-section body.
3. Set `draft: false` when ready to publish (drafts don't appear in listings, but the
   file exists so you can work on it over multiple sessions).
4. Add a `featured.png` image to the same folder.

### Add a publication
1. Add a BibTeX entry to `publications/references.bib`.
2. Copy `publications/_template.qmd` → `publications/your-slug.qmd`, filling in the front
   matter and using `[@your-bibtex-key]` to render a properly formatted citation.

### Update the CV
Export current PDFs from your CV/résumé documents and save them as:
```
files/cv/RicardoPavan_CV_2026.pdf
files/cv/RicardoPavan_Resume_2026.pdf
```
These exact filenames are already referenced in `_variables.yml` (`cv_pdf`, `resume_pdf`) —
no other file needs to change. Update `cv_last_updated` in the same file.

### Change profile links (GitHub, LinkedIn, ORCID, Scholar, email)
Edit the `links:` and `email:` fields in `_variables.yml`.

## Deployment

`.github/workflows/publish.yml` builds the site with Quarto on every push to `main` and
publishes the rendered `_site/` output to the `gh-pages` branch (via
`peaceiris/actions-gh-pages`), keeping build output separate from source.

**One-time setup after creating the repo:**
1. Push this content to `main` (or your working branch first — see below).
2. In the repo's **Settings → Pages**, set the source to **Deploy from a branch**, and
   select **`gh-pages`** (created automatically after the first successful workflow run).
3. Confirm the custom/default URL is `https://ricrocha82.github.io`.

## Recommended Git workflow

```
# from a fresh clone of the new/existing ricrocha82.github.io repo
git checkout -b redesign
# copy this site/ folder's contents into the repo root
git add .
git commit -m "Rebuild site with Quarto: structure, styles, initial content"
git push -u origin redesign
# open a PR, preview, then merge redesign -> main when ready
```

## Quality checks before publishing

```
quarto render                 # build must succeed with no errors
quarto check                  # environment/install sanity check
```
Then manually: click through the nav on mobile width, confirm the CV buttons work (after
adding real PDFs), and skim new pages for placeholder text you meant to replace.

## Troubleshooting

- **"command not found: quarto"** — Quarto CLI isn't installed or not on `PATH`.
- **Python chunk errors on render** — make sure `jupyter`, `matplotlib`, `scikit-learn`
  are installed in the Python environment Quarto is using (`quarto check` shows which one).
- **A new project/post doesn't show up** — check its `draft` field isn't `true`, and that
  the front matter YAML is valid (a stray tab or missing colon will silently break parsing).
- **GitHub Pages shows an old version** — check the Actions tab for a failed workflow run,
  and confirm Pages is set to serve from the `gh-pages` branch, not `main`.

See also `docs/EDITORIAL_GUIDE.md` for writing style, image sizing, and confidentiality
guidance, and `docs/PRIVACY.md` for the analytics policy.
