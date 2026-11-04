# Releasing & update checks

Every copy of Ratatoskr has a version number (footer and **About & license**). It can check a small public file, `ratatoskr.json`, each time an offline copy opens (the hosted version is always current), and show a banner when a newer version exists. No login or credentials are involved.

## One-time setup

1. Publish this repository. The update file must be publicly readable.
2. In `ratatoskr.json`, set `download` to your releases page, e.g. `https://github.com/CAITOUS/Ratatoskr-DNS-Inspector/releases/latest`.
3. In `Ratatoskr.html`, near the top of the script, set:

   ```js
   manifestUrl:'https://raw.githubusercontent.com/CAITOUS/Ratatoskr-DNS-Inspector/main/ratatoskr.json'
   ```

   Leave it as `''` to turn update checks off.

## Publishing a new version

1. In `Ratatoskr.html`, update `version` and `released` in the `RATATOSKR` settings block.
2. Add an entry to `CHANGELOG.md`.
3. Update `ratatoskr.json`:

   ```json
   { "latest": "1.1.0", "released": "2026-12-01", "download": "https://github.com/CAITOUS/Ratatoskr-DNS-Inspector/releases/latest", "notes": "One-line summary shown in the banner." }
   ```

4. Commit and push to `main`.
   - The hosted app on GitHub Pages updates within a minute or two.
   - The **Release** workflow sees a version that hasn't been released yet. It then creates the `v1.1.0` tag and a GitHub Release with `Ratatoskr.html` and `ratatoskr-1.1.0.zip` (app, guides, license), using the CHANGELOG entry as the release notes.
   - Pushes that don't change the version don't create a release. To re-upload assets for the current version, run the workflow manually with **rebuild** ticked.

Copies with an older version show: *"Ratatoskr 1.1.0 is available — Get the update / Later"*.

## Moving the repository

Keep the old `ratatoskr.json` in place and replace its contents with:

```json
{ "moved_to": "https://raw.githubusercontent.com/NEW-OWNER/NEW-REPO/main/ratatoskr.json" }
```

Existing copies follow the pointer (up to three hops). New releases should use the new `manifestUrl`.

