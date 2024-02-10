# Notes to self for this modified version

- Install qmk CLI tool: `python3 -m pip install --user qmk`
- Set up IDE support: `qmk generate-compilation-database -kb framework_rp2040_controller -km default`
- Build: `qmk compile -kb framework_rp2040_controller -km default`
- Flash: `qmk flash -kb framework_rp2040_controller -km default`
    - Press Fn+Right Shift, or plug in again holding C, then mount the drive that pops up.
- Debugging:
    - https://bbs.archlinux.org/viewtopic.php?id=278341 except use this line: `KERNEL=="hidraw*", SUBSYSTEM=="hidraw", MODE="0660", GROUP="input", TAG+="uaccess", TAG+="udev-acl"`  (not sure yet what the tags do)
    - in `info.json`, set `"console": true`
    - in `keymap.c`, in `keyboard_post_init_user`, do `debug_enable=true;`
    - `#include "print.h"` and print with either `print` or `uprintf`
    - `qmk console` before flashing

Resources:
- Arya's controller schematics, esp. `framework_input_brkt` is useful: https://github.com/CRImier/MyKiCad/tree/master/Laptop%20mods/framework_input_controller
- Framework's input cover info: https://github.com/FrameworkComputer/Framework-Laptop-13/tree/main/Mainboard#input-cover-interface
- Framework's EC source code: https://github.com/FrameworkComputer/EmbeddedController
    - https://github.com/FrameworkComputer/EmbeddedController/blob/hx20-hx30/common/i2c_hid_touchpad.c
    - https://github.com/FrameworkComputer/EmbeddedController/tree/hx20-hx30/baseboard/fwk
    - But these seem incomplete.
    - A comment says "touchpad driver is not in gerrit yet, so comment out this for now"
    - But `baseboard/fwk/ps2mouse.c` seems to have something

Touchpad notes:
- `TP_SDA`, `TP_CTL` - I2C pins
- `TP_INT` - set high to disable touchpad

Original readme follows:

# Quantum Mechanical Keyboard Firmware

[![Current Version](https://img.shields.io/github/tag/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/tags)
[![Discord](https://img.shields.io/discord/440868230475677696.svg)](https://discord.gg/Uq7gcHh)
[![Docs Status](https://img.shields.io/badge/docs-ready-orange.svg)](https://docs.qmk.fm)
[![GitHub contributors](https://img.shields.io/github/contributors/qmk/qmk_firmware.svg)](https://github.com/qmk/qmk_firmware/pulse/monthly)
[![GitHub forks](https://img.shields.io/github/forks/qmk/qmk_firmware.svg?style=social&label=Fork)](https://github.com/qmk/qmk_firmware/)

This is a keyboard firmware based on the [tmk\_keyboard firmware](https://github.com/tmk/tmk_keyboard) with some useful features for Atmel AVR and ARM controllers, and more specifically, the [OLKB product line](https://olkb.com), the [ErgoDox EZ](https://ergodox-ez.com) keyboard, and the Clueboard product line.

## Documentation

* [See the official documentation on docs.qmk.fm](https://docs.qmk.fm)

The docs are powered by [Docsify](https://docsify.js.org/) and hosted on [GitHub](/docs/). They are also viewable offline; see [Previewing the Documentation](https://docs.qmk.fm/#/contributing?id=previewing-the-documentation) for more details.

You can request changes by making a fork and opening a [pull request](https://github.com/qmk/qmk_firmware/pulls), or by clicking the "Edit this page" link at the bottom of any page.

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
