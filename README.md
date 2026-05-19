# Coach Ironclad — Marketing Site

A single-page site for the Coach Ironclad Claude skill.  Landing page, install instructions, example prompts, philosophy, and FAQ — all in one polished file.

## What's in here

```
site/
├── index.html       # The full site (HTML + CSS + JS, one file)
├── vercel.json      # Vercel deployment config
├── netlify.toml     # Netlify deployment config
└── README.md        # This file
```

No build step.  No dependencies.  No package manager.  Just static HTML using Google Fonts and inline styles.

## Local preview

Open `index.html` directly in a browser, or run a quick local server:

```bash
# Python
python3 -m http.server 8000

# Node (npx)
npx serve .

# Then visit http://localhost:8000
```

## Deploy to Vercel (fastest path)

**Option A — Drag and drop:**
1. Go to [vercel.com/new](https://vercel.com/new)
2. Drag this folder onto the upload area
3. Click Deploy

**Option B — Vercel CLI:**
```bash
npm i -g vercel
cd site/
vercel
```

Follow the prompts.  First deploy gets you a `*.vercel.app` URL in about 30 seconds.

**Option C — GitHub integration:**
1. Push this folder to a GitHub repo
2. Import the repo on [vercel.com](https://vercel.com)
3. Auto-deploys on every push

## Deploy to Netlify

**Option A — Drag and drop:**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag this folder onto the page
3. Done — Netlify gives you a live URL

**Option B — Netlify CLI:**
```bash
npm i -g netlify-cli
cd site/
netlify deploy --prod
```

**Option C — GitHub integration:**
Same flow as Vercel — connect a repo, auto-deploy on push.

## Deploy to Cloudflare Pages

```bash
npm i -g wrangler
cd site/
wrangler pages deploy . --project-name=coach-ironclad
```

## Deploy to GitHub Pages

1. Push the contents of this folder to a repo's main branch
2. In repo settings → Pages → set source to "Deploy from a branch" → main → root
3. Wait ~1 minute; your site is live at `username.github.io/repo-name`

## Custom domain

After deploying, add a custom domain through your host's dashboard:
- **Vercel:** Project → Settings → Domains
- **Netlify:** Site settings → Domain management
- **Cloudflare Pages:** Pages project → Custom domains

Add the relevant DNS records at your registrar (CNAME or A/AAAA depending on the host's instructions).  TLS provisions automatically.

## Customization

Everything is in `index.html`.  Key edit points:

- **Colors:** CSS variables in `:root` near the top of the `<style>` block.  The accent is `--brass: #D4A24C`.
- **Fonts:** Google Fonts link in `<head>`.  Currently using Fraunces (display serif), Inter Tight (body), JetBrains Mono (data/protocol).
- **Copy:** All text is inline — `<h1>`, hero tagline, framework cards, install steps, FAQ, etc.
- **Prompts:** Each prompt card has a `data-prompt` attribute holding the full text that gets copied to the clipboard.  Edit the visible text and the `data-prompt` value together.

## Analytics

Not included by default.  Drop in your preferred snippet (Plausible, Fathom, Vercel Analytics, GA4) before the closing `</body>` tag.

For privacy-friendly analytics on Vercel: `Settings → Analytics → Enable` is one click and works without code.

## Notes

- Site is fully responsive (single-column on mobile)
- No JavaScript framework — vanilla JS for the scroll reveals and clipboard copy
- Lighthouse-friendly: should hit 95+ on Performance and Accessibility out of the box
- All fonts load from Google Fonts CDN with `preconnect` hints
