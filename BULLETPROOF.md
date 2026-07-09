# BULLETPROOF.md
exoseed-website — deploy & verify

## 1. BUILD CHECK
```bash
ls -1
# must see: index.html, styles.css, README.md
```
if styles.css is missing → styling fails, site looks broken.

## 2. LOCAL PREVIEW
```bash
python3 -m http.server 8080
```
open `http://localhost:8080`

checklist:
- [ ] no product mentions (no Qruzpay, no features, no apps)
- [ ] dark minimal design loads correctly
- [ ] nav + links work
- [ ] mobile palette/stacking ok (shrink browser window)

## 3. DEPLOY

### NETLIFY (current host)
drag folder or `index.html` + `styles.css` to netlify drop UI.

or cli if netlify token is set:
```bash
npx netlify deploy --prod --dir=.
```

### NGINX / CLOUDFLARE (alternative)
copy folder to server path, point domain there:
```bash
rsync -av ./ user@server:/var/www/exoseed.africa/
```
DNS → server IP. SSL via certbot if needed.

### VERCEL
```bash
npx vercel --prod
```

## 4. LIVE VERIFY
visit `https://exoseed.africa`

checklist:
- [ ] page loads (no 404 on styles.css)
- [ ] HTTPS active (no "not secure" warning)
- [ ] responsive on phone
- [ ] no product-specific copy slipped in
- [ ] "Get in touch" mailto works

## 5. ROLLBACK
if latest deploy is cooked:
- Netlify: deploys page → previous deploy → restore
- nginx: `git revert` or drag previous folder back
- vercel: `npx vercel rollback`

## 6. COMMON PITFALLS
- uploading only index.html → styles.css missing = raw html
- hard refresh after deploy (ctrl+shift+r) to clear cache
- don't add tracking, embeds, or external fonts unless asked
- keep it ambiguous: no future CTAs, no product reveals

## 7. CHANGE CONTROL
any copy/design change must pass the live-verify checklist before shipping.
push only after local preview shows clean. no broken state to prod.
