# Agent Handoff

This repository contains a local Chromium browser theme for Chrome and Microsoft Edge.

## Project Goal

Create a browser theme that mimics the color language of classic Windows 95 applications without using Microsoft-owned logos, icons, screenshots, wallpapers, or official branding.

The theme should feel like a retro Windows 95 desktop:

- Navy title bar: `#000080`
- Teal desktop/new tab background: `#008080`
- Gray window chrome and toolbar: `#C0C0C0`
- Black toolbar/window text: `#000000`
- White tab text on inactive navy tabs: `#FFFFFF`

## Current State

The theme is implemented as a color-only Chromium theme in `manifest.json`.

There are intentionally no active theme image assets. Earlier generated PNG assets caused visible repeated striping in the browser UI when Chrome tiled/stretched them. The current approach uses only `theme.colors` for flat fills.

Current commit history:

```text
701bd7e Make inactive tabs blue
4defef7 Create initial Classic 95 browser theme
```

## Important Files

- `manifest.json` - the actual Chrome/Edge theme manifest.
- `README.md` - user-facing local installation instructions.
- `.gitignore` - ignores packaged theme files, local cache artifacts, and old generated asset folders.

## Current Theme Decisions

The inactive/background tabs are navy to match the Windows 95 active title bar feel:

```json
"background_tab": [0, 0, 128],
"background_tab_inactive": [0, 0, 128],
"tab_background_text": [255, 255, 255],
"tab_background_text_inactive": [255, 255, 255]
```

The active tab text is black because the selected tab blends visually with the gray toolbar/window surface:

```json
"tab_text": [0, 0, 0],
"toolbar": [192, 192, 192],
"toolbar_text": [0, 0, 0]
```

The new tab page background uses the classic teal desktop color:

```json
"ntp_background": [0, 128, 128]
```

## How To Test Locally

In Chrome:

1. Open `chrome://extensions`.
2. Enable developer mode.
3. Click `Load unpacked`.
4. Select `/Users/andrew/Desktop/themes`.
5. After edits, click reload on the theme card.

In Edge:

1. Open `edge://extensions`.
2. Enable developer mode.
3. Click `Load unpacked`.
4. Select `/Users/andrew/Desktop/themes`.
5. After edits, click reload on the theme card.

If Chrome or Edge appears to keep stale styling, remove the unpacked theme and load `/Users/andrew/Desktop/themes` again.

## Validation

Use this command after editing `manifest.json`:

```sh
node -e "JSON.parse(require('node:fs').readFileSync('manifest.json','utf8')); console.log('manifest ok')"
```

## Notes For Future Work

- Keep the theme color-only unless there is a clear visual reason to add image assets.
- Avoid `theme_frame`, `theme_toolbar`, or other tiled PNG theme images unless they are tested carefully in the browser.
- Do not use Microsoft logos, Windows logos, original Windows 95 icons, screenshots, or official wallpapers.
- Keep wording such as "inspired by classic 90s desktop colors" rather than implying an official Microsoft or Windows theme.
- If adding images later, verify that they do not tile, stretch, or create repeated bars across the tab strip.
- The user is still actively tuning the visual design, so prefer small focused commits after each accepted visual change.
