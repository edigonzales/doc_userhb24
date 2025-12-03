# Antora Quickstart & Notes

<!-- This file collects practical tips for newcomers so the project remains easy to maintain. -->

## Requirements
- Node.js 18+ (Antora relies on a fairly recent Node runtime).
- Network access to fetch the default Antora UI bundle (configurable in `antora-playbook.yml`).
- A Git client to clone/update the repository when building elsewhere.

## How to build the site locally
1. Install Antora globally or run it with `npx`:
   - `npx @antora/cli@3.1.8 --version` (checks installation).
2. From the repository root, generate the site:
   - `npx antora --fetch antora-playbook.yml`
   - Output lands in `build/site` (see the `output.dir` setting).
3. Serve the static files if you want a quick preview:
   - `npx serve build/site`

## Project layout
- `antora.yml` — Component descriptor (name, version, start page, navigation file).
- `antora-playbook.yml` — Site-wide configuration with comments about each section.
- `modules/ROOT/pages/index.adoc` — Antora start page that reuses the root `README.adoc`.
- `modules/ROOT/pages/userhb24_1.adoc` — Wraps the existing chapter from `docs/` so it appears as its own page in the site nav.
- `modules/ROOT/nav.adoc` — Defines the left-hand navigation items.
- `README.adoc` — Original root document; still the single source that includes the rest of the handbook.

## Authoring tips
- Keep new handbook chapters in `docs/` and wrap them with a short page in `modules/ROOT/pages/` using an `include::../../../docs/<file>.adoc[]` directive. This keeps the nav friendly while preserving the single-source README flow.
- Avoid hard-coding absolute URLs; use `xref:` whenever you add more pages to the module.
- If you add Asciidoc attributes in pages, prefer adding them to the wrapper pages inside `modules/ROOT/pages/` rather than the source files under `docs/` so the README rendering on GitHub remains simple.

## Troubleshooting
- If Antora cannot find a file, verify the relative include paths from `modules/ROOT/pages/` back to `docs/` or the repository root.
- When the UI bundle download fails (offline builds), download the bundle once and set `ui.bundle.url` to a local zip path.
- Clear the `build/` directory when testing layout changes to avoid stale assets.
