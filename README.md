# htmx-weather

A client-side weather forecast app built with [HTMX](https://htmx.org/) and XSLT — no backend, no build step, just HTML.

**[Live Demo](https://barakplasma.github.io/htmx-weather/)**

## What it does

Fetches hourly weather forecast data from the [Israel Meteorological Service (IMS)](https://ims.gov.il) XML API and renders it directly in the browser using XSLT transforms via HTMX's [client-side-templates](https://github.com/bigskysoftware/htmx-extensions/tree/main/ext/client-side-templates) extension. The page loads automatically and displays a table of forecast times, temperatures, and humidity for each location.

## How it works

1. HTMX fires a GET request on page load (`hx-trigger="load"`) to the IMS XML endpoint (via a CORS proxy).
2. The XML response is transformed client-side using an inline XSLT stylesheet (`xslt-template`).
3. The resulting HTML tables are swapped into the page — no JavaScript application code needed.

## Tech stack

- **[HTMX v2](https://htmx.org/)** — HTML-driven interactivity
- **[htmx-ext-client-side-templates v2](https://github.com/bigskysoftware/htmx-extensions/tree/main/ext/client-side-templates)** — client-side XSLT/Mustache rendering
- **XSLT 1.0** — XML-to-HTML transformation in the browser
- **[MVP.css](https://andybrewer.github.io/mvp/)** — minimal classless CSS framework
- **GitHub Pages** — static hosting via GitHub Actions

## Project structure

```
index.html            — Main weather app (XSLT templating)
mustache.html         — Example: Mustache template with a single JSON object
mustache-array.html   — Example: Mustache template with array iteration
.github/workflows/    — GitHub Pages deployment workflow
```

## Browser compatibility

The app uses the browser's native `XSLTProcessor` API. For environments where `XSLTProcessor` is not available (e.g. some embedded webviews), a built-in polyfill automatically falls back to JavaScript-based XML parsing that produces the same output.

## Running locally

Open `index.html` in a browser. No server or build tools required.

## Examples

The repo includes two additional pages demonstrating HTMX client-side templates with [Mustache.js](https://github.com/janl/mustache.js):

- **`mustache.html`** — Fetches a single todo from [JSONPlaceholder](https://jsonplaceholder.typicode.com) and renders it with a Mustache template.
- **`mustache-array.html`** — Fetches a list of users and iterates over the array with `mustache-array-template`.

## License

MIT — Michael Salaverry