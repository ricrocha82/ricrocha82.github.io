# Analytics & Privacy

**Current status: analytics are OFF.**

`_quarto.yml` has an empty `google-analytics.tracking-id`, which means no analytics script
is loaded and no tracking occurs. No cookies, personal data, or visitor information are
currently collected by this site.

## If you decide to turn analytics on

Recommended: a lightweight, privacy-conscious, cookie-free option such as
[Plausible](https://plausible.io) or [Fathom](https://usefathom.com) rather than Google
Analytics, since neither uses cookies or collects personally identifiable information by
default, and both provide a single small script tag.

To enable:
1. Add the provider's script tag to `styles/head-meta.html`.
2. Document here: what is tracked (typically: page views, referrer, country-level location,
   device type — no individual identifiers), why (to see which projects/tutorials get
   attention and whether the CV is being downloaded), and how visitors can avoid it
   (browser "Do Not Track" / ad-blockers typically block these scripts automatically since
   they aren't cookie-based).
3. Consider only tracking specific meaningful interactions rather than every page view:
   CV/résumé downloads, GitHub repository link clicks, software documentation clicks,
   and contact-link clicks are the most relevant events for a career site.

## What NOT to do

Do not add invasive tracking (fingerprinting, cross-site tracking, ad-network pixels, or
any tool that collects visitor PII without clear disclosure).
