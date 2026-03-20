# Quail Ultra

Quail Ultra is a desktop question-bank browser for local HTML/JSON banks, built on the original Quail Electron app and redesigned around a more UWorld-like USMLE solving workflow.

This release line is a late beta, not a 1.0 stable release.

## Status

- Current release channel: `0.9.0-beta.1`
- macOS Apple Silicon build: supported in this repo
- Windows build: alpha, packaged for convenience, not personally tested on hardware

## What Changed From Upstream Quail

- explicit `Tutor`, `Timed`, and `Untimed` block modes
- continuous question -> answer -> explanation review flow
- persistent question rail with status states
- immediate Tutor-mode reveal on the same page
- per-question eliminate controls
- multicolor highlighting persisted per question
- richer progress state with backward-compatible normalization
- updated builder, overview, and previous-block surfaces
- separate app identity so Quail Ultra can coexist with original Quail on the same Mac

## Compatibility

Quail Ultra keeps the original Quail bring-your-own-qbank format:

- `index.json`
- `tagnames.json`
- `choices.json`
- `groups.json`
- `panes.json`
- per-question `*-q.html` and `*-s.html`

Older Quail progress files are normalized on load so legacy sessions remain readable.

## Install

### macOS Apple Silicon

Use the Apple Silicon release `dmg` for the normal installer-style path, or the `zip` if you want the raw app bundle. The packaged app has a separate bundle ID and user-data path from original Quail, so both apps can live on the same Mac.

### Windows

Windows builds are published as alpha artifacts. Prefer the `exe` installer. A `zip` may also be included for fallback/debug use.

They are expected to be functionally close to the macOS build because the app is Electron-based, but they are not hardware-tested in this repo before release. Treat the Windows artifact as preview quality.

## Development

```bash
npm install
npm start
```

Useful checks:

```bash
node --check main.js
node --check newblock.js
node --check examview.js
node --check previousblocks.js
node --check overview.js
```

## Build

Manual Apple Silicon app bundle:

```bash
npm run build:mac-arm64-manual
```

Installer-style macOS distribution build:

```bash
npm run build:mac-dmg
```

Electron Builder targets:

```bash
npm run build:mac-arm64
npm run build:win-x64
npm run build:win-installer
npm run build:win-release
```

## Release Notes

- `Late Beta` means feature-complete enough for real use, but still short of a stable `1.0`.
- macOS is the primary tested target.
- Windows remains `Alpha` until it has direct runtime validation on a Windows machine.
- current public releases are unsigned unless signing credentials are configured for the build environment

## Maintenance Notes

Internal implementation notes live in [AGENTS.md](AGENTS.md).
