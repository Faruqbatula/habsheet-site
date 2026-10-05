# habsheet-site

habsheet.com. Plain HTML, no build, no tooling — each page is one
self-contained file so it loads on one bar of signal with no second request.
Published by GitHub Pages; `CNAME` is what makes this directory habsheet.com,
and the checks below use it to recognise the site.

| file | |
|---|---|
| `index.html` | home — what it is, and the two people worth hearing from |
| `what-it-does.html` | the sheets, the readings, the export, in detail |
| `contact.html` | the ask, for both audiences |
| `privacy.html` | the policy the App Store and Play hold the app to |
| `signin.html`, `account.html` | the subscription pages — **the only pages that may state a price**, and **not published**: see below |
| `pricing.html` | a redirect to contact. Not a page; see below |
| `samples/` | three sample reports, marked SAMPLE on every page |

## Two things to know before editing

**There is no shared stylesheet.** The header, the nav, the footer and the CSS
block are written out in six files and must stay the SAME TEXT. Change one,
change all six.

**The sign-in and account pages are in this repository and not on the web.**
They point at the development project and there is nothing to subscribe to yet,
so `main` carries them and what is published does not. They are kept in step
with the other pages all the same, because the header and footer are copies.

**The pricing page came down on 5 October 2026** — prices are not settled, and a
visitor reading a number nobody is ready to stand behind is worse than reading
none. `pricing.html` was kept as a redirect because the link was live for three
weeks. Nothing links to it, and it states no price.

## The checks live in the app repository

This repository has no tooling in it, so the checking is in `habsheet/scripts`
next door. Run them from there, not from here:

```
node scripts/check-site-layout.mjs      # six pages in a real browser at 390 and 1440px
node scripts/check-price-parity.mjs     # only a page that sells may state a figure
node scripts/check-says-device.mjs      # the account pages say "device", never "tablet"
```

Each takes `--prove`, which sabotages it and requires it to notice. They find
the site beside the app repository, or wherever `HABSHEET_SITE` points.

**A change here can fail a check there.** Adding a page, moving a footer link,
putting a price on the home page or editing one copy of the header are each
caught — and each will fail the app's suite, not anything in this repository.
