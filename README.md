# Tang Nano 20k Wiki

This centralize/meta documentation for the Tang Nano 20k.

Setup
-----

### Prequisites

To flash (linux and windows, not working on MacOS) : [https://www.gowinsemi.com/en/support/download\_eda/](https://www.gowinsemi.com/en/support/download_eda/)

Just get the Programmer (Driver are also include in it for Linux and Windows). The IDE is needed only if you want to recompile.

### Step 1 - Tang Firmware upgrade BL616

(Step to be verified)

Get `firmware.bin` from latest  : [https://github.com/nand2mario/nestang/releases](https://github.com/nand2mario/nestang/releases) 

Use GoWin Programmer to upload firmware in `External Flash Mode`  / `exFlash Erase, Program thru GAO-Bridge` at Start Address : `0x500000` .

![](Tang%20Nano%2020k_image.png)

### Step 2 - M0S Firmware upgrade (USB adaptor)

Hardware :  

*   [https://wiki.sipeed.com/hardware/en/maixzero/m0s/m0s.html](https://wiki.sipeed.com/hardware/en/maixzero/m0s/m0s.html)
*   [https://fr.aliexpress.com/item/1005005142466936.html?gatewayAdapt=glo2fra](https://fr.aliexpress.com/item/1005005142466936.html?gatewayAdapt=glo2fra)

Wiring :

*   [https://github.com/harbaum/FPGA-Companion/tree/main/src/bl616](https://github.com/harbaum/FPGA-Companion/tree/main/src/bl616)

![Tang Nano 20k with M0S Dock](https://github.com/harbaum/FPGA-Companion/raw/main/src/bl616/m0s_dock_tn20k.png)

Firmware  upgrade :

*   Upgrade : [https://github.com/harbaum/FPGA-Companion/tree/main](https://github.com/harbaum/FPGA-Companion/tree/main)
*   Tool to upgrade : [https://github.com/bouffalolab/bouffalo\_sdk/tree/master/tools/bflb\_tools/bouffalo\_flash\_cube](https://github.com/bouffalolab/bouffalo_sdk/tree/master/tools/bflb_tools/bouffalo_flash_cube)
*   Tutorial : [https://youtu.be/WZQhHkECUhQ?si=LT89isD2eEuaMP4H](https://youtu.be/WZQhHkECUhQ?si=LT89isD2eEuaMP4H) 

### Step 3 - Program your core

To test a core use use GoWin Programmer to upload firmware in `SRAM Mode` / `SRAM Program`.

![](2_Tang%20Nano%2020k_image.png)

To program it and make it stay after poweroff use GoWin Programmer to upload firmware in `External Flash Mode`  / `exFlash Erase, Program thru GAO-Bridge` at Start Address : `0x000000` .

![](1_Tang%20Nano%2020k_image.png)

### Step 4 - Upload ROM, Kickstart, DOS - Depends of your core

Use GoWin Programmer to upload in `External Flash Mode`  / `exFlash Erase, Program thru GAO-Bridge` at Start Address : `0x?00000` .  
  
Note : **If you use GoWin Programmer rename your file to a .bin.**

![](3_Tang%20Nano 20k_image.png)

Note for amiga :

*   If using kickstart 1.3 upload it twice at `0X400000` and at `0X440000`.
*   If using kickstart 3.1 upload it once at `0X400000`.

### Step 5 - Hardware Wiring

Thanks to Mister JBam wiring is now quite standard :

![wiring](https://github.com/vossstef/tang_nano_20k_c64/raw/main/.assets/wiring_spi_irq.png)

Step 6 - Shielding
------------------

*   DB9 + Midi Out : [https://github.com/Unixware/nanoshield](https://github.com/Unixware/nanoshield)
*   DB 9 + Midi In + Midi Out : [https://github.com/harbaum/MiSTeryNano/tree/main/board/misteryshield20k](https://github.com/harbaum/MiSTeryNano/tree/main/board/misteryshield20k)

### Step 7 - Using cores

Remember that `F12` is your main key for OSD and change rom, ADF or go to settings.

Appendix
--------

### Table of memory storage


| **Tang 20K Start Adress** | **Filename** | **Description** |
| --- | --- | --- |
| 0X000000 |     | For core (FPGA bitstream) |
| 0X100000 | tos104fr.img | Atari ST ROM |
| 0x200000 | 2dosa\_c.bin | C64 - c1541 Dolphin DOS 2 |
| 0x20C000 | dos1541-325302-01+901229-05.bin | C64 - c1541 CBM DOS 2.6 |
| 0x214000 | C1541.ROM | C64 - c1541 Speed DOS Plus |
| 0x21C000 | JiffyDOS\_C1541.bin | C64 - c1541 Jiffy DOS |
| 0X400000 | kick13.rom / kick31.rom | Amiga Kickstart 1.3 to Amiga Kickstart 3.1 (cover both adresses) |
| 0X440000 | kick13.rom | Amiga Kickstart 1.3 |
| 0x500000 | firmware.bin | Firmware BL616 internal or firmware for NES ? |

Cores available
---------------

*   Amiga  : [https://github.com/harbaum/NanoMig](https://github.com/harbaum/NanoMig)
*   Atari ST  :  [https://github.com/harbaum/MiSTeryNano](https://github.com/harbaum/MiSTeryNano)
*   C64 : [https://github.com/vossstef/tang\_nano\_20k\_c64](https://github.com/vossstef/tang_nano_20k_c64)
*   GBA : [https://github.com/nand2mario/gbatang](https://github.com/nand2mario/gbatang)
*   Linux/Litex : [https://github.com/sipeed/TangNano-20K-example/tree/main/linux/firmware](https://github.com/sipeed/TangNano-20K-example/tree/main/linux/firmware)
*   NES: [https://github.com/nand2mario/nestang](https://github.com/nand2mario/nestang)
*   Pacman : [https://github.com/fjpolo/PacManTang](https://github.com/fjpolo/PacManTang)
*   SNES : [https://github.com/nand2mario/snestang](https://github.com/nand2mario/snestang)

### Tang Nano 20K Documentation

*   [https://wiki.sipeed.com/hardware/en/tang/tang-nano-20k/nano-20k.html](https://wiki.sipeed.com/hardware/en/tang/tang-nano-20k/nano-20k.html)
*   [https://wiki.sipeed.com/hardware/en/tang/tang-nano-20k/example/unbox.html](https://wiki.sipeed.com/hardware/en/tang/tang-nano-20k/example/unbox.html)
*   Q&A : [https://wiki.sipeed.com/hardware/en/tang/common-doc/questions.html](https://wiki.sipeed.com/hardware/en/tang/common-doc/questions.html)

M0S - USB-C - Compatibility list
--------------------------------


| **Hardware** | **Compatible** | **Type** |
| --- | --- | --- |
| 8BITDO NES30 GAMEPAD | **YES** | Joystick |
| Logitech MX Vertical | **YES** | Mouse |
| Riitech - Rii Mini Keyboard | **YES** | Mouse + Keyboard |
| Logitech G915 | **NO** | Keyboard |

### Issues resolution

#### SPI Not Found

If you got `SPI Mode Not Found` error in `External Flash Mode`:

1.  Load hdmi.fs : [https://github.com/sipeed/TangNano-20K-example/raw/refs/heads/main/hdmi/hdmi.fs](https://github.com/sipeed/TangNano-20K-example/raw/refs/heads/main/hdmi/hdmi.fs) in `SRAM Mode` / `SRAM Program` .
    
2.  Load hdmi.hs as `External Flash Mode`  / `exFlash Erase, Program thru GAO-Bridge`.
    

And get back in track.

#### SD Card not working :

For most cores you need to have the M0S micro-controller with an updated firmware.

### Video Channels

Mister JBam Playlist :  [https://www.youtube.com/watch?v=v49ZLia5aPQ&list=PLJGG96sZs\_VJ5RQSccQ0Q9ZUzUBNng4Zk](https://www.youtube.com/watch?v=v49ZLia5aPQ&list=PLJGG96sZs_VJ5RQSccQ0Q9ZUzUBNng4Zk) (french)
