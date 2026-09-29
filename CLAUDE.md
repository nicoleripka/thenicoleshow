# The Nicole Show — website

Live at **https://thenicoleshow.tv** (backup: https://thenicoleshow.netlify.app).
Hosted on Netlify. Domain registered at GoDaddy. This folder lives in iCloud Drive → Projects.

## What's here

| File | What it is |
|---|---|
| `index.html` | The whole page: logo, hanging mic, host portraits, heading, guest list, sponsor. |
| `styles.css` | All styling. Colors, fonts and margins are variables at the top (`:root`). |
| `assets/` | Portrait videos (`portrait-v3.mp4` left, `portrait-v2.mp4` right) and `granola-logo.png`. |
| `netlify.toml` | Tells Netlify to publish this folder as-is (no build step). |

Plain HTML + CSS only. No framework, no build tools, no JavaScript needed.

## Common edits

- **Add a guest:** in `index.html`, find `<ul class="guest-list">`, copy one `<li class="guest">…</li>` block, and change the name and "Title, Company". The grid wraps on its own.
- **Change a guest's title:** edit the `guest-role` text, e.g. `Co-founder &amp; CEO, World Labs`.
- **Swap a host portrait:** put the new video in `assets/`, then update the matching `<video src="…">`. Videos should be muted MP4s with a white/near-white paper background (the page blends white into the background color). Keep files small (under ~1 MB; compress with ffmpeg `-crf 23`, no audio).
- **Background color:** change `--bg` in `styles.css` (currently `#FFFBEF`, "Whisper" light yellow).
- **Fonts:** `--display` (Gambetta: logo, heading, names) and `--text` (Supreme: everything else). Both from Fontshare, stored in `assets/fonts/` and loaded with `@font-face` at the top of `styles.css`.
- **Mic:** the hand-drawn SVG inside `<div class="mic">`. Its length/position is set by the SVG itself (`viewBox` height and the cord path) and `.mic` in `styles.css`. It swings (`.mic-swing`) and its sound bars pulse (`.mic-wave`). It's hidden on screens narrower than 1100px so it doesn't overlap the portraits.
- **"Get in Touch":** a link that opens an email to nicole@sound-ventures.com.

## Design rules (please keep)

- Page background `#FFFBEF`, ink `#111111`, secondary text `#555555`. No other colors unless asked.
- Left/right margin 80px on desktop (24px on small screens). Logo and "Get in Touch" share a baseline.
- Centered text sections. Serif for titles and names, sans for body.
- Respect `prefers-reduced-motion` (animations stop).
- Avoid tiny all-caps letter-spaced labels and italic "accent words"; Nicole finds them templated.

## Publishing

After making changes, preview locally (open `index.html` in a browser), then publish:

```
netlify deploy --prod --dir .
```

First time only on a new computer: `npm install -g netlify-cli`, then `netlify login` (opens a browser to authorize) and `netlify link` (choose the **thenicoleshow** site). After that, just run the deploy command above.

Always show Nicole what changed and get a yes before running the production deploy.
