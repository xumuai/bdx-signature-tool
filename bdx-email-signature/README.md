# BDx Email Signature tool

Static single page. No build step, no dependencies.

## Deploy

**Option A — drag and drop**
1. Go to vercel.com/new
2. Drag this folder onto the page
3. Done. Note the URL it gives you.

**Option B — CLI**
```
npx vercel --prod
```

## Updating

Replace `index.html` and redeploy. Nothing else references it.

## The logo

The wordmark URL is set on one line near the top of the `<script>` block in
`index.html`:

```js
const LOGO_URL = "https://www.xumu.ai/wp-content/uploads/2026/08/bdx-signature-logo.png";
```

This is currently an **interim host**. Before rollout it must be repointed to a
permanent URL on bdxworld.com. Requirements for the file:

- PNG, not SVG (SVG does not render in Outlook or Gmail)
- 168 x 96 px, transparent background, brand blue #2d43e8
- Permanent public URL, no password protection, no query string
- Not a WordPress-generated resize variant — link the original upload

The page echoes the current URL at the bottom so it can be checked at a glance.

## Notes

- `X-Frame-Options: SAMEORIGIN` blocks embedding in Notion. That is intentional:
  clipboard permissions do not work in a cross-origin iframe, so the Notion page
  should link out to this tool rather than embed it.
