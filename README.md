# Yanzhou Mu Personal Homepage

This repository contains the source code for Yanzhou Mu's personal academic homepage.

The site is built with Jekyll and hosted through GitHub Pages. Personal content is maintained in `_config.yml`, `_pages/`, `_publications/`, and `_portfolio/`. Resume source files are kept in `resume/` and are excluded from the generated public site to avoid exposing private resume metadata.

## Local Development

Install Ruby dependencies:

```bash
bundle install
```

Run the site locally:

```bash
bundle exec jekyll serve -l -H localhost
```

The local site is served at `http://localhost:4000`.

## JavaScript Assets

The project keeps the template's small JavaScript bundling workflow:

```bash
npm install
npm run build:js
```

## Website Analytics

This site supports privacy-friendly page view analytics via GoatCounter.

To enable analytics:

1. Create a GoatCounter site.
2. Replace `YOUR_GOATCOUNTER_CODE` in `_includes/analytics-providers/custom.html` with your own GoatCounter site code.
3. Use your deployed domain in the GoatCounter dashboard. For GitHub Pages, this can be `muyanzhou96.github.io`; if you later use a custom domain, use that custom domain instead.
4. Deploy the site to GitHub Pages.
5. View traffic statistics in the GoatCounter dashboard.

The analytics script is loaded asynchronously through the site's shared Jekyll analytics include, and the visit count is not displayed publicly on the website.

## Docker

The project can also run through Docker:

```bash
docker compose up
```

## Content Sources

The current personal content was derived from `resume/main-en.tex`:

* Education
* Research direction
* Project experience
* Publications
* Patents
* Public email address
* Profile photo

Sensitive resume fields such as date of birth, phone number, and detailed address are intentionally not published on the website.

## Theme Attribution

This site is adapted from an open-source Jekyll academic homepage template. The upstream license is preserved in `LICENSE`.
