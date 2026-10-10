# codeforge-bootsraper

CodeForge bootstrap for `com.codeforge.app` — fork of Termux bootstrap rebuilt with correct `$PREFIX`.

Original Termux bootstrap uses hardcoded prefix `/data/data/com.termux/files/usr` and fails on CodeForge with `exec("/data/data/com.codeforge.app/files/usr/bin/login") No such file or directory`. This repo rebuilds bootstrap archives with `PREFIX=/data/data/com.codeforge.app/files/usr`.

## Packages

- `bootstrap-aarch64.zip`
- `bootstrap-arm.zip`
- `bootstrap-i686.zip`
- `bootstrap-x86_64.zip`

Variant: `apt-android-7` (Android 7+)

## Usage

CodeForge `app/build.gradle.kts` downloads from this repo:

```
https://github.com/scto/codeforge-bootsraper/releases/download/bootstrap-v1.118.5/bootstrap-{arch}.zip
```

Checksums are embedded in `app/build.gradle.kts` `downloadBootstrap()` and verified with SHA-256.

## Build

Rebuild bootstrap via `termux-packages`:

```bash
export TERMUX_PREFIX=/data/data/com.codeforge.app/files/usr
export TERMUX_PACKAGE_VARIANT=apt-android-7
./scripts/build-bootstrap.sh
```

CI builds on every tag `bootstrap-*` via `.github/workflows/build.yml`.

## License

GPLv3 — same as Termux.

## Fork

Forked from https://github.com/termux/termux-packages (bootstrap generation scripts).
