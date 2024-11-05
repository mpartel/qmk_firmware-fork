# Notes to self for this modified version

- Install qmk CLI tool: `python3 -m pip install --user qmk`
- Set up IDE support: `qmk generate-compilation-database -kb framework_rp2040_controller -km default`
- Build: `qmk compile -kb framework_rp2040_controller -km default`
- Flash: `qmk flash -kb framework_rp2040_controller -km default` and then do one of these:
    1. (Needed for fresh board) Connect GD and BT while plugging the board in, then mount the drive.
    2. (Works for subsequent flashes) Hold C and plug in the keyboard again, then mount the drive.
- Debugging:
    - https://bbs.archlinux.org/viewtopic.php?id=278341 except use this line: `KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0660", GROUP="input", TAG+="uaccess", TAG+="udev-acl"`  (not sure yet what the tags do)
    - in `info.json`, set `"console": true`
    - in `keymap.c`, in `keyboard_post_init_user`, do `debug_enable=true;`
    - `#include "print.h"` and print with either `print` or `uprintf`
    - `qmk console` before flashing

Original readme follows:

# Quantum Mechanical Keyboard Firmware

[![Current Version](https://img.shields.io/github/tag/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/tags)
[![Discord](https://img.shields.io/discord/440868230475677696.svg)](https://discord.gg/qmk)
[![Docs Status](https://img.shields.io/badge/docs-ready-orange.svg)](https://docs.qmk.fm)
[![GitHub contributors](https://img.shields.io/github/contributors/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/pulse/monthly)
[![GitHub forks](https://img.shields.io/github/forks/qmk/qmk_firmware.svg?style=social&label=Fork)](https://github.com/qmk/qmk_firmware/)

This is a keyboard firmware based on the [tmk\_keyboard firmware](https://github.com/tmk/tmk_keyboard) with some useful features for Atmel AVR and ARM controllers, and more specifically, the [OLKB product line](https://olkb.com), the [ErgoDox EZ](https://ergodox-ez.com) keyboard, and the Clueboard product line.

## Documentation

* [See the official documentation on docs.qmk.fm](https://docs.qmk.fm)

The docs are powered by [VitePress](https://vitepress.dev/). They are also viewable offline; see [Previewing the Documentation](https://docs.qmk.fm/#/contributing?id=previewing-the-documentation) for more details.

You can request changes by making a fork and opening a [pull request](https://github.com/qmk/qmk_firmware/pulls).

## Supported Keyboards

* [Planck](/keyboards/planck/)
* [Preonic](/keyboards/preonic/)
* [ErgoDox EZ](/keyboards/ergodox_ez/)
* [Clueboard](/keyboards/clueboard/)
* [Cluepad](/keyboards/clueboard/17/)
* [Atreus](/keyboards/atreus/)

The project also includes community support for [lots of other keyboards](/keyboards/).

## Maintainers

QMK is developed and maintained by Jack Humbert of OLKB with contributions from the community, and of course, [Hasu](https://github.com/tmk). The OLKB product firmwares are maintained by [Jack Humbert](https://github.com/jackhumbert), the Ergodox EZ by [ZSA Technology Labs](https://github.com/zsa), the Clueboard by [Zach White](https://github.com/skullydazed), and the Atreus by [Phil Hagelberg](https://github.com/technomancy).

## Official Website

[qmk.fm](https://qmk.fm) is the official website of QMK, where you can find links to this page, the documentation, and the keyboards supported by QMK.
