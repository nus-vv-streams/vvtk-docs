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
VVTk is a Toolkit for Volumetric Video Researchers.

## How to Install?

1. Install the latest Rust compiler from the [official website](https://www.rust-lang.org/tools/install)
2. Verify if `cargo` and `rustc` have been installed successfully using `cargo --version` and `rustc --version`
3. If you are using **linux**, make sure `gcc`, `g++`, `cmake`, `libssl-dev`, `pkg-config`, `libfontconfig1-dev` are installed
4. Compile and build the binaries with `cargo build --release --bins`
5. Install the binaries if you want to use it anywhere you want. `cargo install --path .`
6. Use `vv` and `vvplay` in other directory. Now you are good to go!
7. Download the [8i_dataset](https://plenodb.jpeg.org/pc/8ilabs/) to use and test our tool!