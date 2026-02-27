# DeltaScanner — Deploy Checklist

## 1. Activate email capture (Formspree) — 5 min

1. Go to **formspree.io** → log in / sign up (free)
2. Click **New Form** → name it "DeltaScanner Early Access"
3. Copy your Form ID — looks like `xabcdefg`
4. Open `index.html`, find this line near the bottom:
   ```js
   const FORMSPREE_ID = 'YOUR_FORM_ID';
   ```
5. Replace `YOUR_FORM_ID` with your ID, e.g. `'xabcdefg'`
6. Submissions will email you + Formspree dashboard captures all leads

---

## 2. Deploy to Vercel — 10 min

### Option A: Drag & drop (fastest, no Git required)
1. Go to **vercel.com** → New Project
2. Drag the entire `web/` folder onto the deploy zone
3. Done — Vercel gives you a `.vercel.app` URL immediately

### Option B: Git → Vercel (recommended for future pushes)
```bash
# From the deltascanner/ project root
git init
git add web/
git commit -m "add landing page"
# Push to GitHub, then:
```
1. Go to **vercel.com** → New Project → Import Git Repository
2. Select your repo
3. Under **Root Directory**, set it to `web`
4. Click Deploy

---

## 3. Point deltascanner.com → Vercel — 5 min

DNS is already on Cloudflare. In Vercel:
1. Project Settings → Domains → Add `deltascanner.com`
2. Vercel shows you two DNS records to add
3. In **Cloudflare DNS**, add those records (A + CNAME or just CNAME)
4. Set Cloudflare proxy to **DNS only** (gray cloud) for the apex/www records
5. SSL handles itself — takes < 5 min to propagate

---

## Done. Page is live.

Next step per handoff doc: send 5 warm/cold emails with deltascanner.com in the footer.
