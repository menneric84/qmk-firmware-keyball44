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
    $ git clone https://github.com/qmk/qmk_firmware.git --depth 1 --recurse-submodules --shallow-submodules -b 0.22.14 qmk
    ```

    Currently Keyball firmwares are verified to compile with QMK 0.22.14

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
| `KBC_RST`  | `Kb 0`          | `0x7e00` | Reset Keyball configuration[^1]                                   |
| `KBC_SAVE` | `Kb 1`          | `0x7e01` | Persist Keyball configuration[^1] to EEPROM                       |
| `CPI_I100` | `Kb 2`          | `0x7e02` | Increase 100 CPI (max 12000)                                      |
| `CPI_D100` | `Kb 3`          | `0x7e03` | Decrease 100 CPI (min 100)                                        |
| `CPI_I1K`  | `Kb 4`          | `0x7e04` | Increase 1000 CPI (max 12000)                                     |
| `CPI_D1K`  | `Kb 5`          | `0x7e05` | Decrease 1000 CPI (min 100)                                       |
| `SCRL_TO`  | `Kb 6`          | `0x7e06` | Toggle scroll mode                                                |
| `SCRL_MO`  | `Kb 7`          | `0x7e07` | Enable scroll mode when pressing                                  |
| `SCRL_DVI` | `Kb 8`          | `0x7e08` | Increase scroll divider (max D7 = 1/128) <- Most Scroll slow      |
| `SCRL_DVD` | `Kb 9`          | `0x7e09` | Decrease scroll divider (min 0 = 1/1) <- Most Scroll fast         |
| `AML_TO`   | `Kb 10`         | `0x7e0a` | Toggle automatic mouse layer                                      |
| `AML_I50`  | `Kb 11`         | `0x7e0b` | Increase 50ms automatic mouse layer timeout (max 1000ms)          |
| `AML_D50`  | `Kb 12`         | `0x7e0c` | Decrease 50ms automatic mouse layer timeout (min 100ms)           |
| `SSNP_VRT` | `Kb 13`         | `0x7e0d` | Set scroll snap mode as vertical                                  |
| `SSNP_HOR` | `Kb 14`         | `0x7e0e` | Set scroll snap mode as horizontal                                |
| `SSNP_FRE` | `Kb 15`         | `0x7e0f` | Set scroll snap mode as disable (free scroll)                     |

[^1]: CPI, scroll divider, automatic mouse layer's enable/disable, and automatic mouse layer's timeout.

## How to create your keymap

(to be documented)

## Keyamaps

Keyball44 provides some keymaps as default:

* `via` - VIA support, trackball is on right side
* `test` - Test for building/soldering Keyball46 (w/ right trackball)
* `default` - Template for customized keymap (w/ right trackball)
