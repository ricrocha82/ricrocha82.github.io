# Editorial Guide

## Writing style

- Use clear, confident, evidence-based language. Prefer verbs like *developed, designed,
  implemented, analyzed, led, contributed, built, evaluated, collaborated, published,
  maintained.*
- Avoid inflated language: "world-class," "visionary," "revolutionary," "guru," "ninja,"
  "rockstar," "expert in everything," or unsupported impact claims.
- Distinguish clearly among: work you **led**, work you **implemented**, work you
  **supported**, **collaborative** work, **planned** work, and **ongoing** work. Say which
  one applies in every project/publication entry.
- Write for two audiences at once: a recruiter skimming for 60 seconds, and a PI reading
  closely. Lead with the plain-language problem statement; put technical depth after it.

## Image specifications

- **Project/publication card images:** 640×360px (16:9), PNG or JPEG, under 200KB.
- **Profile photo:** square or portrait, at least 400×400px, under 100KB after compression.
- **Favicon:** 64×64px PNG (also fine as a base for a proper multi-size favicon later).
- **Social share card (Open Graph):** 1200×630px.
- Always compress images before committing (`quarto render` doesn't do this for you).
  A quick way: `python3 -c "from PIL import Image; im=Image.open('in.jpg'); im.save('out.jpg', quality=82, optimize=True)"`.

## Alt text

Every `<img>`/`![]()` needs descriptive alt text — describe what the image *shows*, not
"image of X." Decorative images (e.g. generic placeholder tiles) can use empty alt
(`alt=""`) once real photos replace them, but real project/photo images always need
real alt text.

## Project page structure

Every project page follows the same 13 sections (see `projects/_template.qmd`):
Overview → Problem → My role → Dataset → Methods → Workflow diagram → Results →
Challenges → Publications → Code/documentation → Collaborators → Status → Limitations/
confidentiality note. Keep the "My role" section specific and honest — this is the section
hiring managers and PIs read most carefully.

## Tutorial / data-stats post structure

Every post follows the 12-part structure in the relevant `_template/index.qmd`: Problem →
Learning objectives → Prerequisites → Conceptual explanation → Reproducible example → Code
→ Output → Interpretation → Common errors → Limitations → References → Environment.

## Citation practices

- Add new publications to `publications/references.bib` first (BibTeX is the canonical
  source), then create the matching page from `publications/_template.qmd` and cite with
  `[@bibtexkey]` so formatting stays consistent (APA, via `apa.csl`).
- Never fabricate DOIs, co-authors, journal names, or dates. If unsure, leave the field
  blank and mark it `[PLACEHOLDER]` rather than guessing.

## Confidentiality considerations

- Never publish unpublished results, raw data, or participant-identifying information.
- For ongoing/unpublished projects (e.g. pig burn wound microbiome, spinal cord injury
  microbiome, some cyberinfrastructure work), describe **methods and goals in general
  terms** and explicitly note in the "Limitations or confidentiality note" section that
  results are withheld pending publication or due to data-sharing agreements.
- Do not name collaborators, institutions, or funders beyond what they have already made
  public themselves (e.g. in a published paper's author list).
- When in doubt, describe less rather than more — you can always add detail once
  something is published.
