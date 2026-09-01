# Axis Fields — website

Static HTML. No build step, no framework, no dependencies. Edit a file, commit, it's live.

## Files

```
index.html              Home
verified-capture.html   Tier 1
visual-capture.html     Tier 2
work.html               Gillespie and Verrado
contact.html            Inquiry form
assets/style.css        All styling, every page
.nojekyll               Tells GitHub Pages to serve files as-is
README.md               This file
```

## Deploying to GitHub Pages

1. In your repo, delete the old site files (keep `.git`, and keep `CNAME` if one exists).
2. Drag everything in this folder into the repo, including the `assets` folder and `.nojekyll`.
3. Commit.
4. Settings → Pages. Source: **Deploy from a branch**. Branch: **main**, folder: **/ (root)**. Save.
5. Wait two or three minutes, then hard-refresh.

If `.nojekyll` doesn't appear when you drag files in, your file browser is hiding dotfiles. On the GitHub website use **Add file → Create new file**, name it `.nojekyll`, leave it empty, commit.

### Custom domain

If axisfields.com already points at this repo there is a file named `CNAME` containing just the domain. **Do not delete it.** If you delete it by accident, recreate it with one line: `axisfields.com`

## Editing

**Text** is plain HTML. Find the sentence, change it, commit. Don't remove the `<p>` or `<h2>` tags around it.

**Colors and fonts** are all in the `:root` block at the top of `assets/style.css`. Change a hex value there and it updates every page.

**Navigation** is repeated in the header of each page. If you add a page, add the link in all five.

**Footer** is repeated at the bottom of each page. Same rule.

## Before you publish

- [ ] Phone number. Not currently on the site anywhere. Add to `contact.html` and the footer if you want it public.
- [ ] Photos. There are no images yet. See below.
- [ ] Nothing on the site currently claims NDAA compliance, SAM.gov registration, federal readiness or past performance. That was deliberate. Do not add any of it back until each one is documented and current.

## Accuracy numbers

`work.html` has a commented-out block for the Gillespie residuals:

```html
<!-- ACCURACY: once you are ready to publish residuals, uncomment and fill. -->
```

It ships commented out on purpose. The site currently makes no numeric accuracy claim anywhere, which means there is nothing on it you cannot defend today. Fill it in when you have the withheld check point RMSE in hand, and delete the `<!--` and `-->` lines around it.

## Adding images

The layout is built to work without photos, so nothing breaks while you have none. To add one:

1. Put the file in `assets/` (e.g. `assets/gillespie.jpg`).
2. Add this where you want it:

```html
<img src="assets/gillespie.jpg" alt="Gillespie Dam Bridge from the northwest, steel through truss spans over the Gila River">
```

Write a real `alt` description. Screen readers use it and search engines read it.

Keep files under about 400 KB each. Export at 1600 px wide for full-width use, 900 px for anything in a column.

Best candidates: a point cloud or mesh view of the bridge for the home page hero, one field shot showing the base station set up over a monument, one Fairbank exterior.

## Form behaviour

The contact form builds a pre-filled email and opens the visitor's mail application. Nothing is stored or transmitted through a third party, and there is no backend to break.

Trade-off: someone on a device with no mail client configured will see nothing happen. The email address is displayed as plain text directly above the form for that reason.

If you later want inquiries delivered to your inbox without the mail-client step, a form relay service will do it. The script block at the bottom of `contact.html` has a comment marking exactly what to replace.
