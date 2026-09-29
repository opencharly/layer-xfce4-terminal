# layer-xfce4-terminal

The Xfce4 terminal emulator wired into an OpenCharly Sway session.

The `xfce4-terminal` candy installs `xfce4-terminal` and a Sway `config.d`
snippet so the terminal is available in the desktop. It is part of the
`sway-desktop` composition.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `xfce4-terminal` |
| Package | `xfce4-terminal` (fedora) |
| Binary | `/usr/bin/xfce4-terminal` |
| Requires | `pod-sway` |
| Config | `~/.config/sway/config.d/xfce4-terminal.conf` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list — typically
transitively through the `sway-desktop` composition. The named entity is a box:
its `candy:` value is the box BODY (holding `base:` and the nested composition
`candy:` list):

```yaml
my-desktop-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-xfce4-terminal:v2026.243.2104'
```

Then, inside the desktop session:

```bash
xfce4-terminal
```

The candy's `plan:` asserts the binary at `/usr/bin/xfce4-terminal` and the Sway
config snippet at its expected path.

## Layout

- `charly.yml` — the `xfce4-terminal:` candy entity (the `require:`, the
  per-distro package, the `copy:` plan steps, the `check:` assertions) and the
  embedded `xfce4-terminal-skill:` skill entity.
- `xfce4-terminal.conf` — the Sway `config.d` drop-in.
- `CHANGELOG/` — per-CalVer release history.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-selkies:xfce4-terminal`
- `/charly-selkies:sway` — compositor dependency
- `/charly-selkies:sway-desktop` — composition that includes this candy
- `/charly-selkies:thunar` — file manager (also in `sway-desktop`)
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
