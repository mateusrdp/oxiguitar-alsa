# Architecture and strategy

The plugin gives OxiGuitar a list of devices and an audio stream. It is built on the `cpal` audio library, through a small layer that the other output plugins share, and it uses the ALSA host of that library.

The strategy is one output plugin for each system's own sound API, so each can be installed, updated and left out on its own. OxiGuitar picks among the installed outputs.

## Current limitations

- **Exclusive access on some systems.** Without a sound server, ALSA gives a device to one program at a time; another program playing sound may block OxiGuitar, or the other way round.
- **More delay than PipeWire** on PipeWire desktops, where ALSA's sound takes a detour.
- **Your system's sound must already work.** The plugin doesn't repair or configure ALSA.

## Left out on purpose

- **A sound library of our own.** [cpal](https://github.com/RustAudio/cpal), the Rust audio library, already speaks every system's sound API. All four output plugins share a thin layer over it, [oxiguitar-audio-cpal](https://mateusrdp.github.io/oxiguitar-audio-cpal/).
- **One plugin for every system.** Each system's output is a plugin of its own, so each is built, tested, updated and left out on its own, and a Linux install carries no Windows code.
- **Recording.** The output plugins only play. OxiGuitar has no audio input.

## Where you can help

- **Testing on real hardware**, especially unusual sound cards, USB interfaces and Bluetooth headphones. Tell us what worked and what clicked.
- **Lower latency** settings, if you know ALSA well.

Every change needs its tests and a row on the [Features](features.md) page; the [Testing](testing.md) page says how to run them.
