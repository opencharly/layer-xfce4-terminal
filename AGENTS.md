# AGENTS.md — layer-xfce4-terminal

Standalone candy repo for the `xfce4-terminal` layer — the Xfce terminal emulator
wired into a Sway session. The candy lives in `charly.yml` at the repo root: the
`require:` on `pod-sway`, the per-distro package, the `copy:` plan steps, the
`check:` assertions, and the embedded `skill:` entity projected into the
marketplace corpus as `/charly-selkies:xfce4-terminal`.

Canonical files:

- `charly.yml` — the `xfce4-terminal:` candy entity and the
  `xfce4-terminal-skill:` skill entity.
- `xfce4-terminal.conf` — the Sway `config.d` drop-in copied to
  `~/.config/sway/config.d/xfce4-terminal.conf`.
- `CHANGELOG/` — per-CalVer release history.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-selkies:xfce4-terminal` — the owning skill. The package, the Sway
  config snippet, and the desktop composition. Load before editing or
  troubleshooting the layer.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, per-distro `distro:` arms, package/repo
  sections, service declarations). Load before editing any entity field or plan
  step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps are the functional evidence — the binary at
  `/usr/bin/xfce4-terminal` and the Sway config snippet.
- The package is declared on the `fedora` arm only; add arms deliberately if the
  candy is composed on other distros.

## Modify this repo

- Edit the `xfce4-terminal:` candy entity AND the `xfce4-terminal-skill:` skill
  entity in `charly.yml` together. The skill is the projected usage source, so a
  behaviour change not mirrored in the skill leaves the corpus stale.
- A change to the Sway snippet belongs in `xfce4-terminal.conf`; the `copy:`
  destination and `check:` path move with it.
- New behaviour claims belong in the `plan:` as an observable `check:` step, and
  in the skill body.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge on
  PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the PR
  body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
