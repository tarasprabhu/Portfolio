# Portfolio Site

A plain HTML/CSS site — no build step, no framework, no dependencies.
Open `index.html` in a browser to preview it locally, or deploy it with
GitHub Pages (steps below).

## Folder structure

```
portfolio/
├── index.html              ← landing page (your name, intro, project grid)
├── css/style.css            ← all styling for the whole site
├── projects/
│   └── fpv-drone.html       ← the FPV drone case study page
└── images/
    └── fpv-drone/           ← every image + video used on that page
```

Each project gets its own folder under `images/` and its own page under
`projects/`. Nothing is shared between projects except `css/style.css`.

## Editing text

Every page is plain HTML. Open it in any text editor (VS Code, Notepad,
whatever) and edit the text between tags directly — there is no data file
or templating layer to fight with. Look for `<!-- EDIT ME -->` comments in
`index.html` marking the name, subtitle, and intro paragraph.

## Swapping or adding photos

Every image is referenced by a plain, descriptive filename, e.g.:

```html
<img src="../images/fpv-drone/hero-render.png" alt="...">
```

To replace one: drop your new file into `images/fpv-drone/` **using the
exact same filename**, overwriting the old one. Nothing else needs to
change.

To use a different filename instead, just edit the `src="..."` in the
matching `.html` file to point at it.

A spare wide-angle shot of the v1 elliptical joint is also included at
`images/fpv-drone/arm-slot-v1-elliptical-alt-angle.png` in case you prefer
it to the one currently used on the page.

## Adding a new project

1. Duplicate `projects/fpv-drone.html` as a starting template, or start a
   new file — just keep the same `<head>` and the `<link rel="stylesheet"
   href="../css/style.css">` line so it picks up the shared styling.
2. Create a matching folder, e.g. `images/new-project-name/`, and put its
   media there.
3. On `index.html`, copy one `<a class="project-card">...</a>` block,
   point its `href` at the new page, and swap the thumbnail/title/description.

## Deploying with GitHub Pages

1. Create a new repository on GitHub and push this whole `portfolio/`
   folder to it (as the repo root):
   ```
   git init
   git add .
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. On GitHub, go to the repo's **Settings → Pages**.
3. Under "Build and deployment", set **Source** to "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
4. GitHub will publish the site at
   `https://<your-username>.github.io/<repo-name>/` within a minute or two.

Any time you push a change (a new photo, an edited paragraph), the live
site updates automatically — no rebuild step required.

## Notes on the video

`images/fpv-drone/test-flight.mp4` is a few MB. GitHub is fine with files
this size, but if you ever add much larger/multiple video files, consider
hosting them elsewhere (e.g. YouTube, unlisted) and embedding a link or
`<iframe>` instead of committing large binaries to the repo.
