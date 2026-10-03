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

## ⚠️ Before this goes live

Three things are unfinished, and each is a rejection risk if the URLs are
submitted as they stand:

1. **`/privacy` and `/terms` are placeholders.** Each says, loudly, that it is
   not the real document. Replace everything between the `PLACEHOLDER` and
   `END PLACEHOLDER` comments with the finished HTML, keeping the `<h1>` and
   the page head.
2. **`/support` has no contact address.** App Store Connect requires a Support
   URL and a reviewer will follow it; a page with no working route is a
   rejection risk. No address has been invented — replace
   `[SUPPORT ADDRESS TO BE CONFIRMED]` with a real monitored mailbox.
3. **Every page carries `<meta name="robots" content="noindex">`** so the
   placeholders cannot be indexed. **Remove that tag** from each page as its
   real content lands.

**Do not point DNS at this site until 1 and 2 are done.** A page reading "not
yet published" at `fourballer.com/privacy` is worse than no page at all, and
the App Store requires a real document at that URL.

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
