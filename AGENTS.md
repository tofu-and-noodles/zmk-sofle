# AGENTS.md

This is a **personal ZMK keymap** for an Eyelash Sofle split keyboard. It is a
rapid-prototyping, frequently-changing config — not a shared production repo.
Optimize for speed of iteration over process ceremony.

## Workflow

- **Commit straight to `main`.** Do not create worktrees, feature branches, or
  PRs. Make the edit and commit directly on `main`. This overrides any global
  worktree / branch-isolation defaults.
- **Direct merges are allowed.** You may merge branches into `main` directly
  (including fast-forward or `-X theirs` content adoption) without asking for a
  PR. Prefer keeping `main` content-identical to the branch being adopted unless
  told otherwise.
- **Pushing:** local-first. Don't push to `origin` unless asked.
- Follow the repo's conventional-commit style: `feat(keymap):`, `fix(keymap):`,
  `perf(keymap):`, `refactor(keymap):`, etc.

## Branches

- `main` — the live, primary keymap (home-row-mod based). This is what I use.
- `vanilla` — backup of the pre-HRM `main` lineage. Don't delete; it's the
  non-HRM reference.
- `home-row-mods` — historical HRM development branch, now merged into `main`.

## Layout / Build

- Board target: `eyelash_sofle_left` / `eyelash_sofle_right` with `nice_view`
  shield; a Studio-enabled left build and a `settings_reset` build also exist.
  See `build.yaml`.
- ZMK pinned to `v0.3.0` via `config/west.yml`; board module from
  `a741725193/zmk-sofle`.
- Firmware is built via the GitHub Actions "build" workflow — grab artifacts
  from the Actions tab, no local toolchain required.

## Keymap orientation (`config/eyelash_sofle.keymap`)

- 13-column split rows; key positions are 0-indexed across all rows:
  row0 `0–12`, row1 `13–25`, row2 `26–38`, row3 `39–51`, thumbs `52–63`.
- Home-row mods use `hrm_l` / `hrm_r` hold-tap behaviors with positional
  `hold-trigger-key-positions`. The lists intentionally include **all thumb
  positions (52–63)** so same-hand thumb chords (e.g. Opt/Ctrl + Backspace)
  resolve to hold; same-hand *finger* keys stay excluded to prevent roll
  misfires.
- HRM timing knobs live on the `hrm_l` / `hrm_r` nodes: `tapping-term-ms`,
  `quick-tap-ms`, `require-prior-idle-ms`, `hold-trigger-on-release`.
- Layer names are self-describing (`macos`, `windows`, `mac_nav`, `numbol`,
  `mouse-and-media`, `kb_func`, etc.). `keymap-drawer/` holds the generated
  SVG/YAML visualizations, refreshed by the `.github/workflows/draw.yml` action.
