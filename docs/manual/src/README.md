# ALSA audio output plugin

This plugin sends OxiGuitar's sound to your speakers through ALSA, Linux's own sound system.

It uploads nothing and downloads nothing. It only plays sound on your computer.

It is the fallback for Linux systems where PipeWire isn't running. PipeWire desktops pass ALSA's sound on to PipeWire anyway, so it also works there. It is the output the AppImage uses.
