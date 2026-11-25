# Requirements and assumptions

## Requirements

- OxiGuitar 0.23 or later, which reads plugin files as archives (the plugin asks for interface 1.3). See [the OxiGuitar manual](https://mateusrdp.github.io/oxiguitar/).
- Linux, on x86_64 or ARM64.

## Assumptions

- Your system's sound is working already. This plugin doesn't repair it.
- ALSA is the common denominator. On a PipeWire desktop you get the same sound through the PipeWire plugin, with lower latency.
