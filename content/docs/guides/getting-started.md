---
title: "Getting Started"
description: "How to install VVTk"
summary: ""
date: 2024-03-29T15:57:53+08:00
lastmod: 2024-03-29T15:57:53+08:00
draft: false
menu:
  docs:
    parent: ""
    identifier: "installation-1711699073"
    weight: 10
toc: true
seo:
  title: ""
  description: ""
  canonical: ""
  noindex: false
---

## Building VVTk

`vvtk` can only be installed from the source code. The following steps will guide you through the installation process.

### Rust

`vvtk` uses Rust 1.78.0 or later. You can install Rust by following the instructions on the [official website](https://www.rust-lang.org/tools/install).

You can verifu that `cargo` and `rustc` have been installed successfully using `cargo --version` and `rustc --version`

### Gnu Compiler Collection (GCC)

For Linux users, make sure `gcc`, `g++`, `cmake`, `libssl-dev`, `pkg-config`, `libfontconfig1-dev` are installed.  

### Cargo Build

After you have installed the necessary tools, you can build the VVtk binaries with:

```bash
cargo build --release --bins
```

## Installation 

After building the binaries, you can install them using the following command:

```bash
cargo install
```

By default, the binaries will be installed in the `~/.cargo/bin` directory. You can add this directory to your `PATH` to use the binaries anywhere.

Alternatively, you can specify the path where you want to install the binaries:

```bash
cargo install --path <PATH>
```

## Optional Features

`vvtk` has several optional features that can be disabled during the build process. You can disable these features in the `Cargo.toml` file.

### `with-tmc2-rs-decoder`

This feature enables the use of the crate `tmc2-rs`, which is a port of the MPEG TMC2 Reference V-PCC decoder to rust, for V-PCC decoding.  This feature requires `ffmpeg` version 6 (and its associated `libavcodec` and `libavutil`) to be installed on your system.

To disable this feature, add the following to your `Cargo.toml` file:
