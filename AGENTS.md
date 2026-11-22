# ALTIS AVN workspace rules

## Work narrowly

- Search with `rg` first and read only the matching region. Do not dump complete large files.
- Treat generated files and local artifacts as verification targets only. Never use them as the primary source for edits.
- Keep command output bounded with a narrow glob, `head`, `tail`, or a small `sed` range.

## Project roots

- GCS: `GCS_Projects/FLASH6`
- Firmware: `Firmwares/ALTIS_INTELLIGNET3_firmware`
- Shared documents and local artifacts: `Others`

## FLASH6 source of truth

- HTML structure: `GCS_Projects/FLASH6/flash6.html`
- JavaScript source modules: `GCS_Projects/FLASH6/scripts/flash6-*.js`
- CSS source layers: `GCS_Projects/FLASH6/styles/src/*.css`
- Do not directly edit `flash6.runtime.js` or `styles/flash6-app.css`; rebuild them from source.
- Do not search `mobile_app_native/www`, `vendor`, or generated bundles unless a verification specifically requires it.

## FLASH6 verification

Run from `GCS_Projects/FLASH6`:

```bash
node scripts/build-flash6-css.cjs
node scripts/build-flash6-runtime.cjs
node scripts/check-flash6-runtime.cjs
```

## Firmware verification

Run PlatformIO from `Firmwares/ALTIS_INTELLIGNET3_firmware`, never from the workspace root.

