# sentry-keyboard

A reverse engineered PCB for the keyboard that Sentry gave as holiday gift in 2024.

![pcb screenshot](./sentry-keyboard.png)

## Features

- Per key RGB LEDs
- Rotary encoder with switch
- USB host interface connection through picoblade connector.
- Programmable keymap with QMK

## Building the Firmware

The `firmware` directory of this repostiory contains only the files specific
to this keyboards firmware, and does not include all of QMK. To build firmware you
need to have a copy of QMK (lets assume it is at `~/code/qmk)`:

```bash
cp -R firmware/* ~/code/qmk/keyboards/sentry-keyboard
cd ~/code/qmk
qmk compile -kb sentry-keyboard -km default
```

This will compile a `.hex` file that you can flash onto your keyboard

```bash
qmk flash -kb sentry-keyboard
```

Brand new micro controller chips may have not have the bootloader initialized, 
and you'll need to erase the chip first:

```bash
dfu-programmer atmega32u4 erase
```

Once the chip has been erased you can flash the firmware on.

## License

Both the PCB design and firmware are provided under the MIT License
