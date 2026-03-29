# ncSender Scan-to-Mesh Plugin

A repo-ready scaffold for an ncSender plugin that:

- probes a top surface into a sparse point cloud
- builds a heightmap surface
- interpolates Z over XY positions
- compensates G-code to uneven stock
- exports CSV / OBJ / STL
- saves and reloads scan sessions

## Repo layout

- `manifest.json` — plugin metadata scaffold
- `src/index.js` — plugin entry + wiring
- `src/probe-engine.js` — probing planner/state machine
- `src/surface-builder.js` — grid + interpolation + triangulation
- `src/gcode-compensator.js` — compensated G-code generation
- `src/mesh-exporter.js` — CSV / OBJ / STL exporters
- `src/scan-session-store.js` — save/load scan sessions
- `src/ui-controller.js` — UI event wiring shell
- `src/host-adapter.js` — ncSender-specific integration layer
- `src/utils.js` — shared helpers

## Current status

This is a working scaffold, not yet a guaranteed drop-in release for every ncSender build.
The main host-specific work belongs in `src/host-adapter.js`.

## First priorities

1. Wire ncSender machine state and motion APIs in `src/host-adapter.js`
2. Validate probe cycle behavior with air tests
3. Export CSV and inspect the captured surface
4. Enable compensated G-code only after bounds and clamp checks are verified
5. Add optional face-boundary masking after top-profile scanning is stable

## Suggested GitHub repo name

`ncsender-scan-mesh-plugin`

## Quick start: publish to GitHub

Create an empty GitHub repository first, then run:

```bash
git init
git branch -M main
git add .
git commit -m "Initial scaffold for ncSender scan-to-mesh plugin"
git remote add origin https://github.com/YOUR-USERNAME/ncsender-scan-mesh-plugin.git
git push -u origin main
```

## Next implementation milestone

- real host adapter bindings
- minimal panel UI
- dry-run compensation preview
- CSV/OBJ/STL export validation
