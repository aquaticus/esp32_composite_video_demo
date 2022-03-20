# ESP32 Composite Video Demo

This program is an example how to use [ESP32 Composite Video library](https://github.com/aquaticus/esp32_composite_video_lib).

![Demo Slides](https://github.com/aquaticus/esp32_composite_video_lib/raw/main/doc/esp32_composite_video_demo.gif)

## License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

## Requirements

It should work with any EPS32 board with Tensilica core. The test environment was as follows:

| Name | Value  |
|------|--------|
|Chip  |ESP32   |
|Cores |2       |
|RAM   |520 KiB |
|FLASH |4 MiB   |
|Clock |240 MHz |

The project was compiled using [ESP32-IDF](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html#introduction) v4.4.

## Connection

Connect **GPIO25** to composite video input and board **GND** to input GND.

If you use a CINCH (RCA) cable, the video signal goes to the pin in the middle, and GND to the outside metal part.

![ESP32 Board](https://github.com/aquaticus/esp32_composite_video_lib/raw/main/doc/esp32_board_cinch.png)

# Build

Make sure you have ESP32-IDF environment installed.

First clone the repository with 2 submodules: LVGL and Composite Video Library.

```bash
git clone --recurse-submodules https://github.com/aquaticus/esp32_composite_video_demo
```
Build

```bash
cd esp32_composite_video_demo
idf.py build
```

and upload to the board

```bash
idf.py flash
```

# Notes

* By default, the program generates PAL signal.
* If you disable LVGL support, Philips PM5544 test image is displayed.
* Using 16 bit LVGL color depth disables auxiliary buffer (to save memory); this makes tearing effect visible.
* Compilation optimization level must be set to *performance* (`-O2`). This is the default setting for demo project.
