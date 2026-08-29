# Jonathan Comerford, portfolio

A single-page career portfolio covering both tracks: 15 years of commercial sales and
account management, and 10 years of frontline human services. One page, two audiences,
switched with the toggle in the top bar.

Everything is in `index.html`. No build step, no framework, no dependencies except Google Fonts.

## Files

**This folder is the website.** Upload all of it, exactly as it is. Nothing here is
spare, and nothing needs building first.

| File | What it is |
|---|---|
| `index.html` | The whole site. HTML, CSS and JavaScript in one file. |
| `404.html` | Error page, same design language. |
| `favicon.svg` | Tab icon, JC monogram. |
| `robots.txt` | Allows all crawlers, points at the sitemap. |
| `sitemap.xml` | The single page URL. Update `lastmod` when you change the content. |
| `assets/` | The three hero photo sizes, the two background sizes, and the CV PDF. |
| `README.md` | This file. Harmless to upload; delete it if you would rather not. |

The originals, the spare photos and the build notes are in `_archive-not-for-upload/`,
one level up. Keep that folder on your computer. Do not upload it.

## Light and dark

The site follows whatever the visitor's device is set to. Dark phone, dark site. Light
laptop, light site. It switches live if they change the setting while the page is open,
including the hand-drawn charts, and the browser's own address bar is tinted to match.
There is no toggle to press and nothing is remembered between visits, which is what
people expect from a site they are only going to open once.

## Preview it locally

Double-click `index.html`. That works for everything except the CV download on some
browsers. For a proper check, run a local server from this folder:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000`.

## Editing

**Text.** Open `index.html` in any editor and search for the words you want to change.
The page is in document order: hero, proof, timeline, case studies, skills, personal
statement, credentials, contact.

**Numbers.** Do not change a figure unless it is on the CV. Every number on the page is
traceable to `assets/Jonathan_Comerford_Customer_Success_Manager_CV.pdf`.

**Case studies.** Each one is an `<article class="case">`. The visible text sits in the
`<dl class="star">` block: one `<dt>` label and one or more `<dd>` lines. Add a `<dd>`
to add a line; the layout handles it.

**Timeline.** Each role is an `<li class="tl-item">` with `data-track="commercial"`,
`"public"` or `"pivot"`. That attribute drives the colour and the audience filter.

**Adding a role.** Copy an existing `tl-item`, change the text, set `data-track`. The
line, the dot and the filter pick it up on their own; nothing else needs touching.

**Swapping the CV.** Put the new PDF in `assets/` and search `index.html` for
`Jonathan_Comerford_CV.pdf`. There are three links to update.

**Swapping the hero photo.** Replace the three `jonathan-hero-*.webp` files, keeping the
same names and the 4:5 proportion. They are 420, 600 and 900 pixels wide.

## Before you deploy

One job: search `index.html` and `sitemap.xml` for `jonathancomerford.co.uk` and put the
real domain in. It appears in the canonical link, the Open Graph tags, the structured
data and the sitemap. The site works without doing this, but search engines and link
previews will point at the wrong address.

There are also two `<!-- CHECK -->` notes in `index.html` asking you to confirm some case
study detail. Both cards read correctly as they stand, so this is not urgent. The notes
are HTML comments, so nobody visiting the site can see them.

## Deploying

**Cloudflare Pages.** Sign in at dash.cloudflare.com, go to Workers & Pages, Create,
Pages, Upload assets. Name the project, drag this folder in, deploy. Set the custom
domain under the project's settings.

**Netlify.** Sign in at app.netlify.com, go to Sites, Add new site, Deploy manually, and
drag this folder onto the drop area.

Either host will give you a temporary URL immediately.

## Notes

- No cookies, no analytics, no tracking, no third-party scripts.
- **If the animation looks dead, check Windows.** Settings, Accessibility, Visual
  effects, Animation effects. When that is off, Windows tells every website to stop
  animating, and the site obeys. It still fades, counts and draws its charts in that
  mode; what it drops is the moving background, the parallax, the spinning halo behind
  the photo and the buttons that lean towards your cursor. Turn the setting on to see
  all of it. On a Mac the equivalent is System Settings, Accessibility, Display,
  Reduce motion.
- On phones the background wash holds still and the top bar drops its blur, because both
  were costing more than they were worth on a small screen. Measured: average frame time
  down about 40%, worst frames down about 75%. It looks the same at that size.
- The page prints cleanly. Case studies print expanded.
