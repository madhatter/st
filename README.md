# st - personal build

Personal build of [st](https://st.suckless.org) (simple terminal) v0.9.3.

## Patches

| # | Patch | Version | Notes |
|---|-------|---------|-------|
| 01 | [alpha](https://st.suckless.org/patches/alpha/) | 20240814 | Background transparency |
| 02 | [scrollback](https://st.suckless.org/patches/scrollback/) | 0.9.2 | Scrollback buffer (required before ligatures) |
| 03 | [ligatures + scrollback](https://st.suckless.org/patches/ligatures/) | 0.9.3 | Ligatures via HarfBuzz, scrollback-compatible variant |
| 04 | [scrollback-mouse](https://st.suckless.org/patches/scrollback/) | 0.9.2 | Mouse wheel scrolling in scrollback buffer |
| 05 | [externalpipe](https://st.suckless.org/patches/externalpipe/) | 0.8.5 | Pipe terminal content to external programs |
| 06 | [font2](https://st.suckless.org/patches/font2/) | 0.8.5 | Fallback font (e.g. for emoji) |
| 07 | [boxdraw](https://st.suckless.org/patches/boxdraw/) | 0.8.5 | Crisp box-drawing characters; modified for HarfBuzz compatibility |
| 08 | [xresources](https://st.suckless.org/patches/xresources/) | 20230320 | Runtime config via Xresources |

Note: patch 08 (glyph wide support / 2-pass rendering) was dropped — incompatible with the ligatures-scrollback patch which already handles the charlen parameter differently.

## Planned

- **Sixel graphics**: requires replacing patch 02 (`st-scrollback-0.9.2`) with `st-scrollback-reflow-standalone-extended`, which has a different `tscrollup`/`tscrolldown` implementation that is compatible with the sixel patch. The current scrollback patch causes context conflicts with sixel's scroll hooks.

## Dependencies

- `libxft`
- `harfbuzz` (for ligatures)

## Build

```bash
makepkg -si
```
