# Usage

NativeLogi currently keeps the internal CLI binary name from OpenLogi:

```sh
openlogi list
openlogi diag features
openlogi diag dpi
openlogi diag smartshift
```

Run from source:

```sh
cargo run -p openlogi --release -- list
```

Set `OPENLOGI_LOG=debug` for verbose tracing while the internal binary names are
still being migrated.
