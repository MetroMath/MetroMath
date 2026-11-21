# Metro Math

Static website for Metro Math. There is no build step for the pages: open `index.html` in a browser, or serve this folder with any static file server (for example `python -m http.server 8000`).

## Layout

```
index.html            Home
about.html            About
classes.html          Classes
pastcomps.html        Past competitions
questions.html        Past questions and answer keys
team.html             Team
css/
  style.css           Site styles (edit this one)
  bootstrap.min.css   Compiled Bootstrap, used for the grid, mobile menu and carousels
scss/                 Bootstrap source used to generate css/bootstrap.min.css
resources/
  brand/              Logo and hero image
  team/               Team photos, named firstname-lastname
  competitions/       One YYYY-MM folder per competition
competitions-standardized/
  YYYY-MM/            Question sets and answer key for each competition (PDF)
```

The only script is Bootstrap's bundle, loaded from a CDN at the bottom of each page.

## Styles

Colours, fonts and the corner radius are CSS variables at the top of `css/style.css`. The main building blocks:

- `.section` / `.section-white`: page sections, separated by a thin rule.
- `.label`: the small uppercase label with an orange bar above a heading.
- `.button`, `.button-outline`, `.button-small`: links styled as buttons.
- `.card-plain`: white card for classes and partners.
- `.frame`: image box with a fixed shape (see below).

## Images

Every photo sits inside a `.frame`, which has a fixed shape (`frame-wide` 16:9, `frame-square`, `frame-portrait` 4:5, `frame-flyer`, or 4:3 by default). The image is cropped to fill it, so you can replace any picture with one of a different size and the layout will not move. Images that contain text, such as winner slides and flyers, also use `frame-contain` so they are shown whole instead of cropped.

To change a picture, replace the file and keep its name, or change the `src` in the HTML.

- Use lowercase file names with hyphens and no spaces, such as `jane-doe.jpg`. Hosts on Linux treat `Photo.jpg` and `photo.jpg` as different files.
- Use forward slashes in paths: `resources/team/jane-doe.jpg`.
- Give each image a short `alt` description of what it shows.
- For a new competition, create `resources/competitions/YYYY-MM/` with `flyer.png`, `winners-N.png` and `photo-N.jpg` as needed, then copy one `<article class="competition">` block in `pastcomps.html`, put it at the top, and give its carousel a new id such as `winners-2026-01`.

## Past questions

Each competition's files go in `competitions-standardized/YYYY-MM/`, using these names: `grades-3-5-sprint.pdf`, `grades-3-5-target.pdf`, `grades-6-8-sprint.pdf`, `grades-6-8-target.pdf` and `answer-key.pdf`. To add a competition, copy one `<article class="competition">` block in `questions.html`, put it at the top, and change the date and folder in its links. If a round is missing, delete its `<li>` and say so in a `<p class="question-note">` under the list.

## Navigation and footer

Each page has its own copy of the navbar and footer, so make changes to them in all six HTML files. On each page, the current page's nav link has `class="nav-link active" aria-current="page"`.
