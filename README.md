# keyball44

A split keyboard with 44 vertically staggered keys and 34mm track ball.

* Keyboard Maintainer: [@Yowkees](https://twitter.com/Yowkees)
* Hardware Supported: Keyball44 PCB, ProMicro
* Hardware Availability:
  * <https://shirogane-lab.com/>

## How to build

1. Check out this repository.

    ```console
    $ git clone https://github.com/futabooo/keyball.git keyball
    ```

2. Check out [qmk/qmk_firmware](https://github.com/qmk/qmk_firmware/) repository in another place.

    ```console
    $ git clone https://github.com/qmk/qmk_firmware.git --depth 1 --recurse-submodules --shallow-submodules -b 0.16.3 qmk
    ```

    Currently Keyball firmwares are verified to compile with QMK 0.16.3

3. Create a symbolic link to this `keyball/` directory from [qmk/qmk_firmware]'s `keyboards/` directory.

    ```console
    $ ls
    keyball/ qmk/

    $ cd qmk/keyboards
    $ ln -s ../../keyball/qmk_firmware/keyboards/keyball keyball
    $ ls keyball/
    drivers/  keyball44/ lib/
    $ cd ..
    ```

4. `make` your Keyball firmwares.

    ```console
    $ make -j8 SKIP_GIT=yes keyball/keyball44:default
    ```

## Special keycodes

Value    | Keycode    |Description
---------|------------|------------------------------------------------------------------
`0x5DA5` | `KBC_RST`  |Reset Keyball configuration
`0x5DA6` | `KBC_SAVE` |Persist Keyball configuration to EEPROM
`0x5DA7` | `CPI_I100` |Increase 100 CPI (max 12000)
`0x5DA8` | `CPI_D100` |Decrease 100 CPI (min 100)
`0x5DA9` | `CPI_I1K`  |Increase 1000 CPI (max 12000)
`0x5DAA` | `CPI_D1K`  |Decrease 1000 CPI (min 100)
`0x5DAB` | `SCRL_TO`  |Toggle scroll mode
`0x5DAC` | `SCRL_MO`  |Enable scroll mode when pressing
`0x5DAD` | `SCRL_DVI` |Increase scroll divider (max 7 = 1/128)
`0x5DAE` | `SCRL_DVD` |Decrease scroll divider (min 0 = 1/1)

***NOTE***

* The values are for VIA/Remap
* The values are for QMK/0.16.3. It will be different when you use another version of QMK.

## How to create your keymap

(to be documented)

## Keyamaps

Keyball44 provides some keymaps as default:

* `via` - VIA support, trackball is on right side
* `test` - Test for building/soldering Keyball46 (w/ right trackball)
* `default` - Template for customized keymap (w/ right trackball)