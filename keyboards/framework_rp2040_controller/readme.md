# framework_rp2040_controller

![framework_rp2040_controller](https://cdn.tindiemedia.com/images/resize/VOnoDfiY-NV4P8v_Nk-rnflOg8c=/p/full-fit-in/1200x800/i/769311/products/2022-10-21T14%3A52%3A03.200Z-IMG_2099.JPG)

This is RP2040-based a controller for Framework laptop Input Cover, translating keypresses into HID events.

Supported:

* Keyboard
* Fn layers working in the same way as Framework laptop - thanks to DHowett!
* Keyboard backlight, with keyboard control

Yet unsupported:

* Touchpad
* Caps lock LED
* Power button
* RGW LED driving

Supported, doesn't yet depend on this firmware:

* Fingerprint sensor

---------------------------

* Keyboard Maintainer: [Arya](https://github.com/CRImier)
* Hardware Supported: Framework Input Cover Controller board
* Hardware Availability: [Tindie](https://www.tindie.com/products/crimier/framework-input-cover-controller/) or [build yourself](https://github.com/CRImier/MyKiCad/tree/master/Laptop%20mods/framework_input_controller)

Make example for this keyboard (after setting up your build environment):

    make framework_rp2040_controller:default

Flashing example for this keyboard:

    make framework_rp2040_controller:default:flash

See the [build environment setup](https://docs.qmk.fm/#/getting_started_build_tools) and the [make instructions](https://docs.qmk.fm/#/getting_started_make_guide) for more information. Brand new to QMK? Start with our [Complete Newbs Guide](https://docs.qmk.fm/#/newbs).

## Bootloader

Enter the bootloader in 3 ways:

* **Keycode in layout**: Press Fn+Right Shift
* **Physical boot button**: short GND and BOOT pads on the PCB with tweezers/thin scissors while plugging the keyboard in
* **Bootmagic reset**: Hold down the key at (0,0) in the matrix (C) and plug in the keyboard
