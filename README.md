# Retro 95 Browser Theme

Retro 95 Browser Theme is part of the Retro 95 project: a small set of themes inspired by classic 90s desktop colors.

This project is not affiliated with or endorsed by Microsoft.

## Repositories

- Browser theme: [a-gubskiy/retro-95-browser](https://github.com/a-gubskiy/retro-95-browser)
- VS Code theme: [a-gubskiy/retro-95-vs-code](https://github.com/a-gubskiy/retro-95-vs-code)

## Palette

| Surface | RGB | Hex |
| --- | --- | --- |
| Desktop background | `0, 128, 128` | `#008080` |
| Active title bar | `0, 0, 128` | `#000080` |
| Window chrome | `192, 192, 192` | `#C0C0C0` |
| Shadow | `128, 128, 128` | `#808080` |
| Highlight | `255, 255, 255` | `#FFFFFF` |
| Text | `0, 0, 0` | `#000000` |

## Install Locally

1. Open `chrome://extensions` in Chrome or `edge://extensions` in Edge.
2. Enable developer mode.
3. Choose `Load unpacked`.
4. Select this folder.

## Validate

```sh
node -e "JSON.parse(require('node:fs').readFileSync('manifest.json','utf8')); console.log('manifest ok')"
```
