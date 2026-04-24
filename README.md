# st - personal build

Personal build of [st](https://st.suckless.org) (simple terminal) v0.9.3.

## Patches

| # | Patch | Version | Notes |
|---|-------|---------|-------|
| 01 | [alpha](https://st.suckless.org/patches/alpha/) | 20240814 | Background transparency |
| 02 | [scrollback](https://st.suckless.org/patches/scrollback/) | 0.9.2 | Scrollback buffer (required before ligatures) |
| 02b | scrollback-fix-ttywrite | 0.9.3 | Fixes scrollback resets when focus is lost | 
| 03 | [ligatures + scrollback](https://st.suckless.org/patches/ligatures/) | 0.9.3 | Ligatures via HarfBuzz, scrollback-compatible variant |
| 04 | [scrollback-mouse](https://st.suckless.org/patches/scrollback/) | 0.9.2 | Mouse wheel scrolling in scrollback buffer |
| 05 | [externalpipe](https://st.suckless.org/patches/externalpipe/) | 0.8.5 | Pipe terminal content to external programs |
| 06 | [font2](https://st.suckless.org/patches/font2/) | 0.8.5 | Fallback font (e.g. for emoji) |
| 07 | [boxdraw](https://st.suckless.org/patches/boxdraw/) | 0.8.5 | Crisp box-drawing characters; modified for HarfBuzz compatibility |
| 08 | [xresources](https://st.suckless.org/patches/xresources/) | 20230320 | Runtime config via Xresources |
| 09 | sync (custom) | 0.9.3 | DEC private mode 2026 (Synchronized Output) for Neovim; built from scratch for this stack |
| 10 | [csi_22_23](https://st.suckless.org/patches/csi_22_23/) | 0.8.5 | Title stack (CSI 22/23): push/pop window title for programs like Neovim; modified for 0.9.3 stack |

> Note: patch 02b is a minor fix related to patch 02, and is not a separate patch from the original scrollback patch. 
It is of no use without patch 02 and is seperate to keep the original scrollback patch intact for reference.

## Planned

- **Sixel graphics**: requires replacing patch 02 (`st-scrollback-0.9.2`) with `st-scrollback-reflow-standalone-extended`, which has a different `tscrollup`/`tscrolldown` implementation that is compatible with the sixel patch. The current scrollback patch causes context conflicts with sixel's scroll hooks.

## Dependencies

- `libxft`
- `harfbuzz` (for ligatures)

## Build

```bash
makepkg -si
```
