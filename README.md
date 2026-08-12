# BDx Email Signature tool

Static single page that generates the BDx email signature. No build step,
no dependencies.

Live: _(add the Vercel URL here once deployed)_

## Structure

```
index.html    the entire tool — this is the only file that changes
vercel.json   headers + config
```

`index.html` must stay at the repository root. Vercel serves the root directory
for projects with no framework preset; moving it into a subfolder produces a
404.

## Making a change

1. Edit `index.html`
2. Commit and push to `main`
3. Vercel rebuilds and deploys automatically, on the same URL

Every push also gets its own preview URL, so changes can be checked before they
replace production. Previous deployments stay available and can be promoted back
from the Vercel dashboard if a change needs undoing.

## The logo

The wordmark URL is set on one line near the top of the `<script>` block:

```js
const LOGO_URL = "https://www.xumu.ai/wp-content/uploads/2026/08/bdx-signature-logo.png";
```

**This is an interim host.** Before company-wide rollout it must be repointed to
a permanent URL on bdxworld.com. Requirements:

- PNG, not SVG — SVG does not render in Outlook or Gmail
- 168 x 96 px, transparent background, brand blue `#2d43e8`
- Permanent public URL, no password protection, no query string
- Link the original upload, not a WordPress-generated resize variant
- Never moved or renamed — every email ever sent references it

The page prints the current URL at the bottom so it can be checked at a glance.

## Notes

- `X-Frame-Options: SAMEORIGIN` prevents embedding in Notion. This is
  deliberate: clipboard permissions do not work in a cross-origin iframe, so an
  embedded copy would show a copy button that silently fails. The Notion guide
  links out to this tool instead.
- The preview uses an embedded copy of the logo so the page renders even if the
  hosted file is unreachable. The copied signature uses the hosted URL.
