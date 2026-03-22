# CLAUDE.md — IncidentResponse

## Project Overview

This is a **Jekyll / GitHub Pages** redirect site. Its sole purpose is to redirect visitors from the old GitHub Pages URL to the new canonical location at [https://ir.cnd.ca.gov](https://ir.cnd.ca.gov). It is not an application — it is a single-page static site with a meta-refresh redirect.

## Technology

- **Static site generator:** Jekyll (GitHub Pages default)
- **Templating:** Liquid (`{% ... %}` / `{{ ... }}`)
- **No build dependencies** beyond what GitHub Pages provides automatically

## Repository Structure

```
index.html          # Root page (front matter sets redirect target and delay)
Redirect.md         # Markdown front-matter file consumed by the layout
_layouts/
  index.html        # Liquid layout template for the redirect page
```

## How It Works

1. `Redirect.md` defines front-matter variables: `target`, `targetname`, `time` (delay in seconds), `message`, and `targettitle`.
2. The layout `_layouts/index.html` renders an HTML page with a `<meta http-equiv="refresh">` tag that redirects to the target URL after the specified delay.
3. The root `index.html` is a static fallback that also redirects to `https://ir.cnd.ca.gov`.

## Build / Run

No local build step is required. GitHub Pages builds and serves the site automatically on push.

To preview locally:

```bash
# Requires Ruby and Bundler
gem install jekyll bundler
jekyll serve
```

## Tests

There are no automated tests. Verification is manual — confirm the page redirects correctly after deployment.

## Coding Conventions

- HTML uses 4-space indentation.
- Liquid template tags use standard Jekyll conventions.
- Keep the repo minimal; it exists only for the redirect.
