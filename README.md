# iotclass-media

Generated media for [IoTClass.org](https://iotclass.org): narration audio, character voice lines, captions and 3D character models.

**This repository holds binaries only as GitHub Release assets.** Its git tree is just this README, `LICENSES.md` and one small index JSON per release under `releases/`. No audio, video or 3D files are ever committed to git history, and Git LFS is not used.

## How it links to the site

1. A GPU session generates files from source kept in a content repo (`iotclass-characters`, `iotclass-animated-lessons`).
2. The files are published here as a release, one tag per batch, e.g. `audio-mqtt-narration-v1`. Every file's sha256 and size are recorded before upload and checked after.
3. In [`iotclass`](https://github.com/ngcharithperera/iotclass), a `gpu/*` branch adds one row per file to `assets/data/media-manifest.json` (schema: `schemas/media-manifest.schema.json`, gate: `scripts/check-media-manifest.py`). Each row's `url` is `<tag>/<file>`, resolved against the manifest's `mediaBase` (`https://github.com/ngcharithperera/iotclass-media/releases/download/`).
4. The main IoTClass session reviews every row (listens, watches, checks licences) and sets `approved: true`. The site plays only approved rows.

## Layout

| Path | What |
|---|---|
| `README.md` | This file |
| `LICENSES.md` | Every model used, its version and licence, and whether IoTClass.org CIC may use its output |
| `releases/<tag>.json` | Index of one release: file names, sha256, bytes, mime, duration, model, settings, source repo and commit |

## Rules

- Only models whose licence allows use by IoTClass.org CIC (education, possibly commercial). No cloning of a real person's voice.
- Raw masters and anything irreplaceable also go to the founder's Box.
- Maximum 2 GB per release asset.
