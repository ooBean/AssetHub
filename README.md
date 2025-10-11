# AssetHub — Static Assets Repository

This repository is a central place to store static visual assets used across projects and pages. Assets include SVGs, images (jpg, png, avif, etc.), and fonts (woff/woff2/ttf), as well as CodePen example resources.

## Purpose

- Provide a structured location for reusable visual assets.
- Keep naming conventions and usage examples for quick referencing and integration.
- Offer a simple contribution and commit convention (Conventional Commits).

## Top-level directories

Example directories in the repository:

- `cats/` — theme or demo folders (organize images by theme)
- `fonts/` — font files and related CSS/instructions
- `portfolio/` — example or portfolio images
- `svg/` — all SVG assets, organized by project or theme, e.g. `svg/codepen_demo/spooky-clock/`

> Note: You can add subfolders as needed to group assets by theme or component.

## Usage examples

Directly reference an image in HTML:

```html
<!-- Relative path example (depends on the location of the referencing file) -->
<img src="./svg/codepen_demo/spooky-clock/jack-o'-lantern.svg" alt="jack o'lantern">
```

Use an SVG as a CSS background:

```css
.header-logo {
  background-image: url("../svg/codepen_demo/spooky-clock/midnight.svg");
  background-size: contain;
  background-repeat: no-repeat;
}
```

Inline SVG (more control over styling and animation):

```html
<!-- Copy the <svg> content from the file and paste into HTML -->
<div class="icon">
  <!-- <svg ...> ... </svg> -->
</div>
```

Self-hosted fonts example (placed under `fonts/`):

```css
@font-face {
  font-family: 'MyAssetFont';
  src: url('./fonts/MyAssetFont.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

## Naming and organization recommendations

- Use lowercase letters and hyphens (-) to separate words, e.g. `jack-o-lantern.svg` (avoid spaces and special characters when possible).
- Create subfolders by theme or usage, e.g. `svg/icons/`, `svg/illustrations/`, `fonts/ui/`.
- For a set of related files, keep them in the same folder and use consistent prefixes to make bulk searches easier.

## Using assets from the web (GitHub Raw / CDN)

If you reference these assets directly from other projects via an online URL (e.g. GitHub raw links or CDNs), you can use the following examples:

- raw.githubusercontent example (note URL encoding for special characters):

```html
<img src="https://raw.githubusercontent.com/ooBean/AssetHub/main/svg/codepen_demo/spooky-clock/jack-o%27-lantern.svg" alt="jack o'lantern">
```

- jsDelivr CDN example (recommended for caching and stability):

```html
<img src="https://cdn.jsdelivr.net/gh/ooBean/AssetHub@main/svg/codepen_demo/spooky-clock/jack-o%27-lantern.svg" alt="jack o'lantern">
```

Notes:
- Prefer pinning to a tag or commit hash (e.g. `@v1.0.0` or `@<commit-hash>`) instead of `@main` to avoid accidental breaking changes.
- Percent-encode special characters in file names when used in URLs (`'` → `%27`, space → `%20`).
- raw.githubusercontent may not set CORS headers needed for fonts or fetch/XHR usage; consider using jsDelivr for those cases.
- Use versioned URLs on CDNs to avoid cache inconsistencies.
- Verify licenses before serving assets publicly.

## Contribution workflow (adding new assets)

1. Add files to the appropriate folder (e.g. `svg/<your-theme>/` or `fonts/<type>/`).
2. Ensure filenames follow the naming guidelines.
3. Commit with Conventional Commits. Examples (PowerShell syntax):

```powershell
# Add a single file
git add svg/your-folder/your-file.svg
git commit -m "feat(assets): add <your-file> for <theme>"

# Or add a whole folder
git add svg/your-folder/
git commit -m "feat(assets): add <theme> assets (svg/images)"

git push origin main
```

Conventional Commits examples:

- feat(assets): add spooky-clock SVG icons
- docs: add README for asset hub
- fix(assets): correct filename for tombstone.svg
- chore: organize fonts folder

## Versioning & License

This repository is a static assets store and doesn't contain runtime code. When copying assets to other projects, ensure you comply with any licensing terms. Add a LICENSE file if you want to explicitly declare usage terms.

## Further notes

- Prefer relative paths when referencing assets inside projects to make snippets portable.
- If the repository grows large, consider adding an index in the README or generating an `assets.json` manifest for automation.

