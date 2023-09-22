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
    $ git clone https://github.com/qmk/qmk_firmware.git --depth 1 --recurse-submodules --shallow-submodules -b 0.22.3 qmk
    ```

    Currently Keyball firmwares are verified to compile with QMK 0.22.3

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

| Keycode    | Value on Remap  | Hex      | Description                                                       |
|:-----------|:----------------|:---------|:------------------------------------------------------------------|
| `KBC_RST`  | `Kb 0`          | `0x7e00` | Reset Keyball configuration                                       |
| `KBC_SAVE` | `Kb 1`          | `0x7e01` | Persist Keyball configuration to EEPROM                           |
| `CPI_I100` | `Kb 2`          | `0x7e02` | Increase 100 CPI (max 12000)                                      |
| `CPI_D100` | `Kb 3`          | `0x7e03` | Decrease 100 CPI (min 100)                                        |
| `CPI_I1K`  | `Kb 4`          | `0x7e04` | Increase 1000 CPI (max 12000)                                     |
| `CPI_D1K`  | `Kb 5`          | `0x7e05` | Decrease 1000 CPI (min 100)                                       |
| `SCRL_TO`  | `Kb 6`          | `0x7e06` | Toggle scroll mode                                                |
| `SCRL_MO`  | `Kb 7`          | `0x7e07` | Enable scroll mode when pressing                                  |
| `SCRL_DVI` | `Kb 8`          | `0x7e08` | Increase scroll divider (max D7 = 1/128) <- Most Scroll slow      |
| `SCRL_DVD` | `Kb 9`          | `0x7e09` | Decrease scroll divider (min 0 = 1/1) <- Most Scroll fast         |

***NOTE***

* The values are for VIA/Remap
* The values are for QMK/0.22.3. It will be different when you use another version of QMK.

## How to create your keymap

(to be documented)

## Keyamaps

Keyball44 provides some keymaps as default:

* `via` - VIA support, trackball is on right side
* `test` - Test for building/soldering Keyball46 (w/ right trackball)
* `default` - Template for customized keymap (w/ right trackball)
