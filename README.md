# fourballer.com

Static site for the Fourballer app's **privacy policy**, **terms of service**
and **support** page. Plain HTML and one stylesheet — no build step, no
dependencies, no external requests (not even a web font: a privacy policy has
to render in exactly the kind of locked-down browser where a font host is
blocked).

Served by GitHub Pages from `main`. A push deploys.

## Why this repo is separate, and public

The app lives in `PadraigKerr/FourBaller`, which is **private**. GitHub Pages
from a private repository needs a paid GitHub plan, so the site is a separate
public repo. Nothing here is secret — these pages are published by definition.

**The app's draft legal documents are deliberately NOT copied here.**
`docs/legal/*-DRAFT.md` in the app repo are marked "NOT REVIEWED BY A LAWYER,
DO NOT PUBLISH AS-IS". The finished copy replaces the placeholders below.

## Layout

```
index.html        landing page
privacy/          /privacy  — App Store Connect "Privacy Policy URL" (required)
terms/            /terms
support/          /support  — App Store Connect "Support URL" (required)
style.css         design tokens copied from the app's theme.js
CNAME             fourballer.com
.nojekyll         serve files as-is, no Jekyll processing
```

Directories rather than `privacy.html` so the URLs are clean
(`fourballer.com/privacy`) without server-side rewriting.

## Before this goes live

1. ~~**`/privacy` and `/terms` are placeholders.**~~ **Done, 3 Oct.** Bruce's
   finished documents are published, effective 3 October 2026. His prose is
   verbatim — verified word-for-word against his files. The only markup change
   was converting literal `- ` bullets, which his markdown-to-HTML converter had
   left as text inside `<p>`, into real `<ul>` lists; no words were altered.
   The amber banner on `/support` is gone with them.
2. ~~**`/support` has no contact address.**~~ **Done.** `/support` now links
   `support@fourballer.com` (Microsoft 365, confirmed working). App Store
   Connect requires a Support URL and a reviewer will follow it, so this had
   to be a real monitored mailbox rather than an invented one.
3. ~~**Every page carries `noindex`.**~~ **Done, 3 Oct** — removed from all
   four pages now that the real documents are published.

**DNS is now the only thing left.** The three content blockers above are
cleared, so the site is ready for the apex records to move — Patrick's hands,
at GoDaddy. Enforce HTTPS can be switched on once the certificate provisions.

## DNS

The domain's nameservers stay at GoDaddy. Only the website records change —
the apex `A` records and `www`. **`MX`, `SPF` and the Microsoft 365
verification `TXT` must be left alone**: the domain runs M365 email, and
moving nameservers or clearing records would break it.

## Local preview

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```
