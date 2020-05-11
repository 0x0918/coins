# ledger-rs

Communication library between Rust and Ledger Nano S/X devices

# Building

Windows is not yet supported.

- Install dependencies
  - Linux
    - `$ sudo apt-get install libudev-dev libusb-1.0-0-dev`
  - OSX
    - TODO
    - please file an issue if you know. I don't have a macbook :)
- Build with native transport
  - `cargo build`
- Install wasm-pack
  - [Link here](https://rustwasm.github.io/wasm-pack/installer/)
- Build with node WASM bindings to `@ledgerhq/hw-transport-node-hid`
  - `wasm-pack build --scope summa-tx --target nodejs -- --features=node --no-default-features`
- Build with browser WASM bindings to
  - `wasm-pack build --scope summa-tx --target bundler -- --features=broswer --no-default-features`

# Features

The `node` and `browser` features are mutually exclusive. You must specify
exactly one, as well as the `--no-default-features` flag.

When building for non-wasm architectures, a native HID transport is compiled
in. When building wasm via `wasm-pack`, you must specify whether you want the
node or browser wasm transport.

# Testing

- run the unit tests
  - `$ cargo test -- --lib`
- run the integration tests
  - Plug in a Ledger Nano S or X device
  - Unlock the device
  - Open the Ethereum application on the device
    - If you don't have the application, [install Ledger Live](https://support.ledger.com/hc/en-us/articles/360006395553) and follow [these instructions](https://support.ledger.com/hc/en-us/articles/360006523674-Install-or-uninstall-apps)
  - `$ cargo test`

# License Notes

This repo was forked from [Zondax's repo](https://github.com/Zondax/ledger-rs)
at commit [`7d40af96`](https://github.com/Zondax/ledger-rs/commit/7d40af9653d04e2d40f8b0c031675b6ff82d7f2c).
Their code is reproduced here under the terms of the Apache 2 License. Files
containing elements from their code maintain their original Apache 2 license
notice at the bottom of the file.

Further work by Summa is available under the GNU LGPLv3 license.

These changes are as follows:
- Remove bip44 crates
- Significant refactoring to all other crates
- Crates have been moved to be modules of a single crate