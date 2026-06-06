# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

**Studio Icons V2** is a Visual Studio Code **file icon theme** extension. It ships the
official icons from the [Visual Studio 2015 Image Library](https://learn.microsoft.com/en-us/previous-versions/visualstudio/visual-studio-2015/designers/the-visual-studio-image-library?view=vs-2015),
recolored to look good across VS Code's dark, light, and high-contrast themes.

It is a maintained fork of the now-unmaintained
[jtlowe/studio-icons](https://github.com/jtlowe/studio-icons), re-published to the
VS Code Marketplace under the publisher `vigan-abd` (extension id `vscode-icon-v2`).

This is **not** a TypeScript/JS runtime extension — there is no `activate()` entry point.
A VS Code icon theme is purely declarative: `package.json` points at a generated JSON
mapping (`fileicons/studio-icons.json`) that maps file extensions / names / folders to SVG
icon files. The only "code" here is a small build pipeline that generates that JSON plus
per-theme SVG variants.

## Commands

```bash
npm run compile    # gulp default: clean + build (regenerate fileicons/)
npm run build      # gulp build only
npm run clean      # gulp clean: remove the generated fileicons/ dir
npm run lint       # standard (StandardJS)
npm run lint:fix   # standard --fix
```

There are no tests. Packaging for the Marketplace is done with `vsce` (not wired into npm
scripts); `.vscodeignore` excludes `src/`, `gulpfile.js`, and `node_modules/` from the
published `.vsix` so only the generated `fileicons/` and `images/` ship.

The project is ESM (`"type": "module"`); all source uses `import`/`export`.

## Architecture / build pipeline

The repository has two halves: **source** (`src/`, edited by hand) and **generated output**
(`fileicons/`, produced by the build — do not edit by hand).

- `src/svg/` — ~90 hand-authored "light/base" SVG icons (e.g. `CSharp_16x.svg`). Colors in
  these files use the literal hex values defined under `colors` in `src/icon-settings.json`.
- `src/icon-settings.json` — the single source of truth. Contains:
  - `colors`: the canonical hex values used inside the source SVGs (background, foreground,
    outline, and brand colors like `cppPurple`, `csGreen`, `tsOrange`, …).
  - `dark` / `light` / `contrast`: per-theme color overrides plus the default
    folder / folder-expanded / root-folder / file icon filenames.
  - `iconDefinitions`: array mapping each `iconPath` (an SVG in `src/svg/`) to the
    `fileExtensions`, `fileNames`, `folderNames`, and/or `folderNamesExpanded` it applies to.
- `src/icon.builder.js` — the `IconBuilder` class that does all the work (invoked by gulp).
- `src/constants.js` — ESM `__dirname` / `__filename` helpers.
- `gulpfile.js` — thin wrapper exposing `clean`, `build`, and the default `series(clean, build)`.

### What `build` does (`src/icon.builder.js`)

1. `clean()` deletes the entire `fileicons/` directory.
2. For every entry in `iconDefinitions`, reads the source SVG from `src/svg/` and writes
   **three** recolored variants into `fileicons/images/`:
   - `<name>.svg` — light theme (replaces background + foreground colors).
   - `<name>_inverse.svg` — dark theme (replaces white/background/foreground/outline and all
     brand colors with the brighter `dark.colors` values).
   - `<name>_contrast.svg` — high-contrast theme (flattens brand colors to the background and
     uses pure black/white foreground + outline).
   This is why `fileicons/images/` has ~3× the file count of `src/svg/`.
3. `_createConfig` writes `fileicons/studio-icons.json`, the VS Code icon-theme manifest:
   an `iconDefinitions` block plus theme mappings. The **dark** mapping is the top-level
   default; `light` and `highContrast` are nested keys, matching VS Code's icon-theme schema.
   `_createThemeMapping(type)` builds each mapping by iterating `iconDefinitions` and applying
   the appropriate filename postfix (`""`, `_inverse.svg`, or `_contrast.svg`).

The recoloring is plain string replacement (`String.replaceAll`) of hex codes — so a source
SVG must use the exact hex values from `icon-settings.json`'s `colors` for theming to work.

## How to add or change an icon

1. Add the new `.svg` to `src/svg/` (use the existing icons' hex palette so recoloring works).
2. Add or edit its entry in `src/icon-settings.json` under `iconDefinitions` with the
   relevant `fileExtensions` / `fileNames` / `folderNames` / `folderNamesExpanded`.
3. Run `npm run compile` to regenerate `fileicons/`.
4. Commit both the source change and the regenerated `fileicons/` output.

Never edit files in `fileicons/` directly — they are overwritten on every build.

## Conventions

- Lint with StandardJS (no semicolons, 2-space indent) — run `npm run lint` before committing.
- `package.json` and `src/icon-settings.json` use tab indentation; leave them as-is.
- Keep README's "Build" steps and this file in sync if the pipeline changes.
