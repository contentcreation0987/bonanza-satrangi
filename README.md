# Bilal Ghazi — portfolio

Static single-page site. No build step, no framework, no `package.json`.
Everything is `index.html` (CSS and JS inline) plus the `assets/` folder.

## Deploy — GitHub → Vercel

**1. GitHub**

Create a new repo (e.g. `bilal-portfolio`), public or private. Upload the
contents of this folder so the repo root looks like:

```
index.html
assets/
README.md
```

Important: `index.html` must sit at the **repo root**, not inside a subfolder.

Via the GitHub website: **Add file → Upload files**, drag `index.html` and the
`assets` folder in, commit.

Or on the command line:

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
6. Root Directory: **leave as is** (`./`)
7. **Deploy**

That's it — no environment variables, no settings. Every future `git push` to
`main` redeploys automatically.

## One thing still to fill in

Search `index.html` for `class="ph"` — placeholders render in ochre on a tinted
background so they're impossible to miss:

- **Three result lines**, one per case study. One sentence each.
- **Photography and Styling credits** on each case study.
- **Resume link** in the contact section (`href="#"` → your PDF or Drive URL).

Email and phone are already in.

## Swapping the intro for a different application

`<section id="intro">` is fenced by comment banners — it's the only block that
changes. Edit the name and the single role line inside it. Nothing below depends
on it.

## Media notes

- Reels show a poster frame immediately; the video file only downloads when it
  comes within 400px of the viewport, then plays muted and loops. This is what
  keeps the page usable on slow mobile data.
- Poster frames were auto-extracted about a second into each film. Swap them for
  hand-picked frames if you want tighter control.
- Case 02 (Lyari) is stills only — no 9:16 film was supplied, and the page says
  so rather than faking one.
- Several stills are Instagram screen captures and carry app chrome. Replace with
  original exports when you have them.
- Total media weight is roughly 40 MB. If first load feels slow on 3G, convert the
  PNG stills to WebP and re-encode the MP4s smaller.
