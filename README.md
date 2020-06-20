# Handwired 5x12 Ortholinear Keyboard

This repo contains layout-specific files and a build log for an Atmel-AVR based handwired 50% ortholinear keyboard similar to the [Preonic](https://drop.com/buy/preonic-mechanical-keyboard). Keyboard firmware used is the open-source [QMK](https://qmk.fm/), maintained by Jack Humbert of [OLKB](https://olkb.com/) along with the MK community.  

## BOM
* 1x [Pro Micro 5V 16MHz](https://www.amazon.com/KeeYees-ATmega32U4-Development-Microcontroller-Bootloader/dp/B07FXCTVQP)
* 1x set [Preonic Plate + Case](https://github.com/olkb/olkb_parts/tree/master/preonic)
* 60x Switches (used [Outemu Ice V2](https://mehkee.com/collections/switches-and-parts/products/outemu-v2-ice-switches?variant=31136134234177))
* 60x [1N4148 Diodes](https://www.mouser.com/ProductDetail/ON-Semiconductor-Fairchild/1N4148?qs=i4Fj9T%2FoRm8RMUhj5DeFQg%3D%3D)
* Wires (used 22AWG solid core)
* 10x M2 6mm screws
* 5x M2 Female Brass Standoffs 12mm
* 1x Micro USB Cable
* 1x Keycap set

### Additional Tools
* [Ender 3 Pro](https://www.creality3dofficial.com/products/creality-ender-3-pro-3d-printer)
* [Station 60 Soldering Station](https://www.circuitspecialists.com/60_Watt_Soldering_Station.html)
* [Kester 44 63/37 Solder](https://www.amazon.com/gp/product/B0149K4JTY/)
* [Overture Black](https://www.amazon.com/dp/B07PGY2JP1/) + [Overture Orange](https://www.amazon.com/OVERTURE-Filament-Consumables-Dimensional-Accuracy/dp/B07VJYL11F/) PLA Filament
* Multimeter
* [Klein Tools Wire Stripper/Cutter](https://www.amazon.com/dp/B00080DPNQ/)
* Flush Cutter
* Screwdriver
* Hot Glue / [Superglue](https://www.amazon.com/Gorilla-Super-Glue-Gram-Clear/dp/B00OAAUAX8)
* Heat Gun / Lighter

## Assembly
1. 3D print or source out case and switch plate. If 3D printing, making the plate thicker to reduce flexing is recommended.

![Case](/images/case.jpg) ![Plate](/images/plate.jpg)  

2. Loop anode end (non-black line side) of 1N4148 diode to one leg of the switch as shown. Solder, and repeat for all switches. Solder cathode ends (black line side) together to form diode rows. Check for continuity from end to end.

![Diode rows](/images/dioderows.jpg)  

3. Solder column wires as shown to other leg of the switches. Keeping insulation between connections is recommended. Check for continuity from top row switch leg to bottom row switch leg for each column.

![Columns](/images/cols.jpg)  

4. Pick 17 I/O pins on Pro Micro for each row and column. Pro Micro pinout information can be found on [Deskthority](https://deskthority.net/wiki/Arduino_Pro_Micro). Measure leads to respectable lengths, then cut and solder onto microcontroller board.

![Pro Micro](/images/promicro.jpg)  

5. Solder wires created in step 4 to each row and column. Test each connection for continuity.

![Pro Micro Connected](/images/promicro_rowcol.jpg)

6. Follow QMK's environment setup and firmware building [tutorial](https://beta.docs.qmk.fm/tutorial/newbs).
7. If new to QMK, setup basic firmware structure for handwired builds in QMK's [handwiring guide](https://beta.docs.qmk.fm/using-qmk/guides/keyboard-building/hand_wire#getting-some-basic-firmware-set-up).
8. Setup keyboard layers as desired. Use [Keyboard Layout Editor](http://www.keyboard-layout-editor.com/#/), [QMK Configurator](https://config.qmk.fm/#/1upkeyboards/1up60hse/LAYOUT_60_ansi), and [QMK basic keycodes](https://beta.docs.qmk.fm/using-qmk/simple-keycodes/keycodes_basic) as help.
9. In config.h, change MATRIX_ROWS, MATRIX_COLS, MATRIX_ROW_PINS, and MATRIX_COL_PINS as wired.
10. Short GND and RST to bring the Pro Micro into bootloader mode.
11. Use [QMK Toolbox](https://qmk.fm/toolbox/) or other methods listed in the QMK [flashing guide](https://beta.docs.qmk.fm/using-qmk/guides/flashing/flashing) to flash the bootloader.
12. Use [QMK Keyboard Tester](https://config.qmk.fm/#/test) to test if each key works as intended. If a key does not work, check wiring for continuity, switches if working, and code.
13. Once working, prepare case by screwing in M2 screws from below to brass standoffs inside.
14. Place plate into case, lining up Pro Micro to port hole in the rear of the case. Screw M2 screws to secure plate.

![Assembled Plate](/images/assembleplate.jpg)  

15. Place keycaps onto switches.

![Final Assembly](/images/finalassembly.jpg)  

## References
* [Pro Micro Information](https://deskthority.net/wiki/Arduino_Pro_Micro)  
* [QMK Toolbox](https://qmk.fm/toolbox/)  
* [QMK Configurator](https://config.qmk.fm/#/1upkeyboards/1up60hse/LAYOUT_60_ansi)  
* [KB Firmware Builder](https://kbfirmware.com/)  
* [Keyboard Layout Editor](http://www.keyboard-layout-editor.com/#/)  
* [In-depth Handwiring Guide](https://imgur.com/a/qcgdF)  
* [How to Handwire a Planck](https://blog.roastpotatoes.co/guide/2015/11/04/how-to-handwire-a-planck/)  
* [Keyboard Matrix Info](https://beta.docs.qmk.fm/developing-qmk/for-a-deeper-understanding/how_a_matrix_works)  
