# Fourai website

A single-page, self-contained company website. The page lives in `index.html`. Your company name, logo and email are set in `config.js`, and the logo files are `logo.png`, `logo-dark.png` and `favicon.png`.

## Preview locally
Double-click `index.html` to open it in any browser. No build step or server is needed.

## Publish
Upload `index.html` to any static host:
- **Netlify**: drag the folder onto app.netlify.com/drop
- **GitHub Pages**: push to a repo, then Settings > Pages > deploy from branch
- **Cloudflare Pages, Vercel, or any web server**: serve the folder as-is

## Company name, logo and email
Open `config.js` and edit:

```js
window.SITE_CONFIG = {
  name: "Fourai",                 // page title and intro text
  legalName: "Fourai LLC",        // footer copyright line ("" = same as name)
  logo: "logo.png",               // header logo, light theme
  logoDark: "logo-dark.png",      // header logo, dark theme ("" = same as logo)
  favicon: "favicon.png",         // browser-tab icon ("" = use the logo)
  showName: false,                // true = also show the name as text beside the logo
  email: "info@fourai.io"
};
```

Included logo files:
- `logo.png`: full logo (icon and wordmark) with a transparent background, 353 x 128 px.
- `logo-dark.png`: the same logo with white lettering, for the dark theme.
- `favicon.png`: the icon on its own, 128 x 128 px, for the browser tab.
- `logo.svg`: the earlier placeholder mark, used only if no PNG can be found.

To swap in a new logo, replace these files (keep the same names) or point `config.js` to new file names. Use PNGs with a transparent background, at least 64 px tall. The header shows the logo 40 px tall (up to 200 px wide). If a file can't be found, the page tries `logo.png`, then `logo.svg`, and finally shows a built-in mark.

Keep `config.js` and the logo files in the same folder as `index.html` when you upload the site.

Search engines and link previews read the name from the page's original HTML, not from `config.js`. The HTML already says "Fourai"; if you rename the company later, also update the `<title>` and `<meta>` tags at the top of `index.html`.

## Fonts
The page uses the Geist and Geist Mono typefaces from Google Fonts. When it's offline, or Google Fonts is blocked, it falls back to the system font automatically.

## Light and dark themes
The page follows the visitor's device setting. The moon/sun button in the header switches themes manually, and the choice is remembered in that browser.

## Announcing products later
In the `<script>` near the bottom of `index.html`, find `const SOLUTIONS = [ ... ]`.
While the list is empty, the page shows the "Something exciting is on the way" teaser.
Add an entry and the teaser is replaced by product cards with stage filters:

```js
const SOLUTIONS = [
  {
    name: "Product name",
    category: "Short label",
    summary: "One or two sentences on what it does.",
    features: ["Tag", "Tag"],
    status: "live",            // discovery | building | pilot | live
    url: "https://product.example.com"  // leave "" until ready
  }
];
```
