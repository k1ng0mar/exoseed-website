# ExoSeed Africa Website (Minimal + Plain CSS)

Clean, ambiguous landing page. Matches the current live site vibe at https://exoseed.africa/ but actually looks presentable.

## Key points
- No product mentions at all (kept completely ambiguous)
- Almost zero CTAs — only subtle "Get in touch" links
- Uses the exact core description from the live site
- Proper vanilla CSS (no Tailwind, no CDNs for styles)
- Single clean HTML + external CSS file

## Files
- `index.html` — markup
- `styles.css` — all styling (dark, minimal, professional)

## Preview
```bash
cd /home/ubuntu/exoseed-website
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy
Drag the whole folder to Netlify, or point your server/Cloudflare to serve the folder for `exoseed.africa`.

Fully self-contained now (no external style dependencies).