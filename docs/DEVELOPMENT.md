# Developing NativeLogi

NativeLogi is an early fork of OpenLogi. The public app name is NativeLogi, but
the internal Rust crate and binary names still use `openlogi` while the codebase
is being migrated.

## Toolchain

- Stable Rust, edition 2024, MSRV 1.85.
- macOS 13 or newer.
- Xcode 16+ with the Metal Toolchain component for GPUI shader compilation.
- `create-dmg` only when building a DMG.

## Build

```sh
cargo build -p openlogi-agent -p openlogi-gui --release
```

Run the CLI inventory command:

```sh
cargo run -p openlogi --release -- list
```

Run the desktop UI:

```sh
cargo run -p openlogi-gui --release
```

On macOS, `.cargo/config.toml` launches `openlogi-gui` through a lightweight dev
bundle so the Dock and menu bar can use the app metadata. Set
`OPENLOGI_DEV_BUNDLE=0` to run the raw binary.

## Checks

Before publishing changes:

```sh
cargo fmt --all -- --check
cargo test -p openlogi-core -p openlogi-agent-core -p openlogi-hook
cargo build -p openlogi-agent -p openlogi-gui --release
```

## App Icon

The canonical NativeLogi icon is:

```text
assets/brand/nativelogi-icon.png
```

Regenerate the macOS icon bundle with:

```sh
cargo run -p xtask -- macos-icns
```

## Packaging

Unsigned local bundle:

```sh
cargo run -p xtask -- bundle-macos
```

Optional DMG packaging:

```sh
cargo run -p xtask -- package-macos
```

Relevant environment variables:

- `NATIVELOGI_SIGN_IDENTITY`: Developer ID signing identity.
- `NATIVELOGI_DMG_BACKGROUND_URL`: optional DMG background image URL.
- `NATIVELOGI_BUNDLE_ASSETS=1`: bundle device renders instead of fetching on demand.
