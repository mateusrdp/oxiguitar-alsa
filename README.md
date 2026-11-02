# oxiguitar-alsa

The ALSA audio output plugin for [OxiGuitar](https://github.com/mateusrdp/oxiguitar), a free, open-source guitar tablature and score viewer, editor and player for Windows, macOS and Linux. It plays OxiGuitar's sound through ALSA, Linux's own sound system: the fallback where PipeWire is not running, and what the AppImage uses (PipeWire desktops pass ALSA's sound on to PipeWire).

- Plugin file `audio-alsa.oxp`, id `oxiguitar.audio-alsa`, Linux only (x86_64 and ARM64). It offers the device list and the stream to the player; the Tools, Plugins window and the footer's output chooser pick the device.
- It shares its code with the other outputs, [oxiguitar-pipewire](https://github.com/mateusrdp/oxiguitar-pipewire), [oxiguitar-wasapi](https://github.com/mateusrdp/oxiguitar-wasapi) and [oxiguitar-coreaudio](https://github.com/mateusrdp/oxiguitar-coreaudio): a stream on one of cpal's hosts, in `oxiguitar-audio-cpal`, which lives in the OxiGuitar repository and is tagged with the SDK.
- It plays sound only on your machine: it uploads and downloads nothing.

## Install

Every [release](https://github.com/mateusrdp/oxiguitar-alsa/releases) holds a zip per Linux processor (x86_64 and ARM64), a `.deb` and an `.rpm` for each, and a `SHA256SUMS` file. The OxiGuitar manual's [install page](https://mateusrdp.github.io/oxiguitar/installing.html) says which one to use and how to keep the plugin updated through your package manager. The plugin needs OxiGuitar 0.11 or later (plugin interface 1.4).

## Build and test

Rust 1.99 or later from [rustup](https://rustup.rs). The plugin SDK comes from OxiGuitar's repository by git tag (`v0.11.0`); nothing of OxiGuitar's is on crates.io.

```sh
cargo test          # unit tests, and the contract suite on the built .oxp file (needs libasound2-dev on Debian and Ubuntu, alsa-lib-devel on Fedora)
./build-oxp.sh      # dist/audio-alsa-VERSION-SYSTEM-ARCH.oxp
```

## History

This plugin lived in the [OxiGuitar repository](https://github.com/mateusrdp/oxiguitar) until its version 0.11.0. Its history came along; an issue number such as `mateusrdp/oxiguitar#123` in an old commit message is in that repository.

## Licence

GPL-3.0-or-later. See LICENSE. Contributions are welcome under the same terms; see [CONTRIBUTING.md](CONTRIBUTING.md).
