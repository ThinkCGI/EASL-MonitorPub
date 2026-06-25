# EASL-MonitorPub — hosting files

These two files are what Chrome downloads to install/update EASL Monitor. Upload the
**contents of this folder** to the root of the public repo `ThinkCGI/EASL-MonitorPub`
and turn on GitHub Pages.

Files:
- `EASL-Monitor.crx` — the packed extension
- `update.xml` — points Chrome at the `.crx` (codebase already set to the Pages URL)

## One-time setup

1. Create the public repo **ThinkCGI/EASL-MonitorPub** (already in progress).
2. Upload `EASL-Monitor.crx` and `update.xml` to the repo root.
3. Repo **Settings → Pages**: set **Source = Deploy from a branch**, branch `main`,
   folder `/ (root)`, then Save.
4. Wait ~1 minute. Confirm both URLs load in a browser:
   - https://thinkcgi.github.io/EASL-MonitorPub/update.xml
   - https://thinkcgi.github.io/EASL-MonitorPub/EASL-Monitor.crx  (should download)

Once those work, the Windows installer (`../installer/`) and the Mac profile are already
pointed at this URL — just run them on the target machines.

## Releasing a new version later

1. Re-pack in `../build` (`node pack.js`) after bumping `version` in
   `EASL Monitor/manifest.json`.
2. Copy the new `dist/EASL-Monitor.crx` here and bump `version` in this `update.xml`
   to match.
3. Commit/upload both (overwrite the existing files — the Pages URLs stay the same).
4. Installed machines pick up the new version automatically on Chrome's next update check.

Note: the published files are world-readable (anyone with the URL can download the `.crx`).
The repo source/history is the only thing the public/private setting affects.
