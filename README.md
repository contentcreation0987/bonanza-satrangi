# Bilal Ghazi — portfolio

Static single page. No build step, no framework, no `package.json`.
`index.html` holds all CSS and JS inline; everything else is in `assets/`.

## Deploy — GitHub → Vercel

**1. GitHub**

New repo (e.g. `bilal-portfolio`). Upload the contents of this folder so the
repo root looks like:

```
index.html
assets/
README.md
```

`index.html` must be at the **repo root**, not in a subfolder.

Website route: **Add file → Upload files**, drag `index.html` and the `assets`
folder in, commit.

Command line:

```
git init
git add .
git commit -m "portfolio"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/bilal-portfolio.git
git push -u origin main
```

**2. Vercel**

1. vercel.com → **Add New… → Project**
2. Import the repo
3. Framework Preset: **Other**
4. Build Command: **leave empty**
5. Output Directory: **leave empty**
6. Root Directory: leave as `./`
7. **Deploy**

No environment variables, no config file. Every push to `main` redeploys.

---

## Still to fill in

Search `index.html` for `class="ph"` — placeholders render in ochre on a tinted
background, impossible to miss.

**1. Three scope lines** — one under each case-study title, in the near-black
break. State what was delivered for that single launch date: how many films,
stills and product shots.

**2. Two result lines.** The Adeel line ("Sold out.") is done. Still open:
- Lyari — `[ADD REACH OR SELL-THROUGH]`
- Retro State — `[ADD RESULT]`

**3. The Lyari 9:16 films.** Nothing Lyari was in the uploads — of the videos
supplied, two turned out to be more Adeel × Movement footage and three were
unrelated real-estate clips. The film row is built and waiting: three slots
across, on the light ground, same weight as the Adeel row. Put the MP4s in
`assets/reels/`, then replace each

```html
<div class="slot"><span>9:16 film<br>[ADD FILE]</span></div>
```

with

```html
<video data-src="./assets/reels/YOUR-FILE.mp4"
       poster="./assets/reels/YOUR-FILE-poster.png"
       muted loop playsinline preload="none"></video>
```

The same markup is in an HTML comment directly above that row.

**4. `assets/bilal-ghazi-cv.pdf`** — the Resume (PDF) link in the contact
section points here. Drop the file in with exactly that name.

---

## Swapping the intro

`<section id="intro">` is fenced by comment banners — the only block that
changes between applications. Edit the name and the single role line inside it.
Nothing below depends on it.

## How the media behaves

- Reels paint their poster frame immediately. The MP4 only downloads once it
  comes within 400px of the viewport, then plays muted and loops, and pauses on
  the way out. This is what keeps the page usable on slow mobile data.
- Poster frames were auto-extracted about a second into each film — swap them
  for hand-picked frames if you want tighter control.
- Several stills are Instagram screen captures and carry app chrome (carousel
  dots, tagged-user badges). Replace with original exports.
- Media is roughly 45 MB. If first load drags on 3G, convert the PNG stills to
  WebP and re-encode the MP4s smaller — no code change needed, just keep the
  filenames.
