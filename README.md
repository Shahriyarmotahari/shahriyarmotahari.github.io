# Shahriyar Motahari — personal website

A single-page academic website with no build step. Everything lives in `index.html`: the content, styles and a small script for dark mode and section highlighting.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole website |
| `photo.jpg` | Your portrait, shown at the top of the page |
| `images/` | Photos used in the galleries (talks, projects, and so on) |
| `favicon.svg` | Browser tab icon (SM monogram) |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is |

## Put it online with GitHub Pages (free)

1. Create a GitHub account if you don't have one.
2. Create a new **public** repository named exactly `<your-username>.github.io`.
3. Click **Add file → Upload files**, drag in everything from this folder (including `.nojekyll`), and commit.
4. Open **Settings → Pages** and confirm the source is the `main` branch, root folder.
5. After a minute or two the site is live at `https://<your-username>.github.io`.

**Alternative:** drag this folder onto [Netlify Drop](https://app.netlify.com/drop) to get a live URL instantly.

## Common edits

All edits happen in `index.html`. Search for the text you want to change.

**Change your photo:** replace `photo.jpg` with another picture using the same file name. A 4:5 (portrait) crop works best. If the face sits too high or too low in the frame, search for `object-position: center 18%` and change the percentage.

**The 3D molecule:** the PFOA model at the top of the page is drawn by a small script inside `index.html` — no plugin or internet connection needed. Visitors drag to rotate, scroll to zoom, and double-click to reset. Search for `mol3d` to find its code, `RADII` or `--mol-c` to change atom sizes and colours, and `--stage` for the soft tint behind it. The viewer height is set by `.mol3d { height: ... }`. A flat drawing of the molecule shows instead if a visitor has JavaScript turned off.

**Project details:** each project in the Research section shows a short summary, and the longer text, image and bullet points sit inside a `<div class="project-body">` that opens when the title is clicked. To add a project, copy a whole `<article class="project">` block and give its button's `aria-controls` and the body's `id` a new matching name.

**Add a photo gallery to a section:** put the picture in the `images/` folder (a 4:3 landscape crop, about 1000 px wide, works best), then copy this block into the section:

```html
<div class="gallery">
  <figure class="shot">
    <button class="shot-btn" type="button" data-full="images/YOUR-PHOTO.jpg" data-cap="Longer caption shown when the photo is enlarged.">
      <img src="images/YOUR-PHOTO.jpg" alt="Describe the photo" loading="lazy" decoding="async" width="1000" height="750">
    </button>
    <figcaption><b>Short label</b> — the rest of the caption.</figcaption>
  </figure>
</div>
```

A gallery fits up to three photos per row and stacks on phones. Clicking a photo enlarges it.

**Add a downloadable CV:** add `cv.pdf` to the folder. Then add this button next to the LinkedIn button in the hero:

```html
<a class="btn btn-ghost" href="cv.pdf">Download CV</a>
```

Your current CV lists your phone number, so remove it first if you want it kept off the web.

**Add a news item:** copy one `<li>` inside `<ul class="news">` and edit the date and text. Newest items go first.

**Add a talk or paper:** copy one `<li class="pub">` block in the Talks section. Your own name is wrapped in `<b>` so it shows in bold.

**Card look:** every card on the page (projects, the teaching card, the service list, the contact box) shares one set of variables near the top of the file: `--radius-card` for the corner, `--line` and `--line-soft` for the hairlines, `--card-bg` for the fill and `--shadow-card` for the light-mode shadow. In dark mode the shadow is switched off and cards are set slightly lighter than the page instead. Change these once and the whole page follows.

**Change the accent colour:** edit `--accent` in the `:root` block near the top. The dark-mode value appears twice further down.

**Update the footer date:** search for `Last updated`.
