# Muhammad Bilal — portfolio

Static single page. `index.html` holds every line of CSS and JS inline.
No framework, no build step, no `package.json`, no bundler.

Contents:

```
index.html
assets/adeel/       14 stills — Adeel uz Zafar collaboration
assets/campaign/     8 stills — Lyari, Retro State
assets/reels/        9 films + 9 poster frames
README.md
```

Every one of the 40 media paths in `index.html` resolves to a file in here.

---

## Deploy — GitHub → Vercel

**1. GitHub**

New repo (e.g. `muhammad-bilal-portfolio`). Upload the contents of this folder
so the repo root looks like:

```
index.html
assets/
README.md
```

`index.html` must sit at the **repo root**, not inside a subfolder.

Website route: **Add file → Upload files**, drag `index.html` and the `assets`
folder in, commit.

Command line:

```
git init
git add .
git commit -m "portfolio"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/muhammad-bilal-portfolio.git
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

No environment variables, no `vercel.json`. Every push to `main` redeploys.

---

## Two things to add before you send the link

**1. `assets/muhammad-bilal-cv.pdf`**

The "Resume (PDF)" link in the contact section points at this exact path. It is
the only dead link on the page. Export the CV, name it exactly
`muhammad-bilal-cv.pdf`, drop it in `assets/`.

**2. The Lyari media**

No Lyari footage or product stills were in the uploads — every supplied video is
Movement × Adeel uz Zafar, Retro State, or unrelated real-estate clips. Case 02
therefore runs on its one back-print still and is visibly the lightest of the
three studies. The scope line states the ten films as delivered work; the page
does not fake them.

To add films, drop the MP4s in `assets/reels/`, grab a poster frame for each,
and paste a row into the Lyari `<article>`:

```html
<div class="reels rv">
<video data-src="./assets/reels/YOUR-FILE.mp4"
       poster="./assets/reels/YOUR-FILE-poster.png"
       muted loop playsinline preload="none"></video>
<!-- repeat per film -->
</div>
<div class="cap"><p>Caption.</p></div>
```

For stills, copy the `<div class="rows rv">` block from Case 03 and swap the
filenames. Both patterns already appear in the file — copy, don't write new.

---

## Swapping the intro for another application

`<section id="intro">` is fenced by comment banners and is the only block that
changes between applications. Edit the name and the single role line inside it;
its styles are the `#intro` rules in the `<style>` block. Nothing below depends
on it.

## How the page behaves

- **Reels** paint their poster frame immediately. The MP4 downloads only once it
  comes within 400px of the viewport, then plays muted, loops, and pauses on the
  way out. This is what keeps it usable on slow mobile data.
- **Reveals** are fades only — no parallax, no scroll-jacking, no page
  transitions, no cursor effects. If the document loads hidden (background tab,
  email preview, crawler) every section reveals immediately instead of staying
  blank.
- `prefers-reduced-motion` disables the reveals entirely.

## Known rough edges in the media

- Poster frames were auto-extracted about a second into each film. Swap them for
  hand-picked frames if you want tighter control — same filename, no code change.
- Several stills are Instagram screen captures and carry app chrome (carousel
  dots, tagged-user badges). Replace with original exports when you have them.
- Media is roughly 45 MB. If first load drags on 3G, convert the PNG stills to
  WebP and re-encode the MP4s smaller, keeping the filenames.
