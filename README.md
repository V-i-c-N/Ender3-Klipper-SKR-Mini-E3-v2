# Ender 3 Klipper
## Orange Pi Setup
1. download armbian for orange pi https://www.armbian.com/orange-pi-3/ (KIAUH likes Debian the most).
2. flash it to an SD.
    ```bash
    ouch d Armbian_community_25.8.0-trunk.228_Orangepi3_bookworm_current_6.12.30_minimal.img.xz #unpack - yoy can use other software
    sudo dd status=progress if=Armbian_community_25.8.0-trunk.228_Orangepi3_bookworm_current_6.12.30_minimal.img of=/dev/<your disk> # flash to SD
    ```
3. Put SD into Orange PI and turn it on. After it turns on, initial config will be started. E.g. set a root password, timezone etc.
4. To add another Wi-Fi run `armbian-config` and the add it in the GUI.
5. `nand-sata-install` to move system from SD card to emmc (internal oragePi flash storage)
6. Install [Avahi](https://wiki.archlinux.org/title/Avahi) to get mDNS working and use orangepi3.local instead of IP to connect to the printer.
7.  install klipper
    ```bash
    git clone https://github.com/dw-0/kiauh
    ./kiauh/kiauh.sh
    ```
Done :D You can open your printer in the browser and setup printer.cfg file
## Raspberry Pi setup
1. Run `rpi-imager` and flash mainsail to a raspberry pi.
2. Connect to it via ip in the browser or <hostname>.local
3. setup printer.cfg in Machine config
4. ssh into RPi
    ```bash
    cd ~/klipper
    make menuconfig; # follow instructions from printer.cfg - which is based on SKR-mini-E3-v2.0 example from clipper repo
    make; #create out/klipper.bin
    cp out/klipper.bin sd_card/firmware.bin;
    ```
## SKR Mini E3 v2.0 setup
Insert the SD to the SKR board. It will flash itself.

## Useful links:
- BLTouch on Klipper: https://www.youtube.com/watch?v=iEo7tJ0wbPU
- Klipper config reference: https://github.com/Klipper3d/klipper/blob/master/docs/Config_Reference.md
- ender3 example: https://github.com/Klipper3d/klipper/blob/5d0d6d5a32930a9daa249e20148457a754beaac3/config/printer-creality-ender3-2018.cfg#L1
- SKR-mini-E3-v2 example: https://github.com/Klipper3d/klipper/blob/dd03cca49b920762f959d8cce047a6cc4debf60b/config/generic-bigtreetech-skr-mini-e3-v2.0.cfg
- Klipper remaining time gcode: https://gist.github.com/lhess/9d2fe36094cf05bcf0a7d8c2e64ac5d6

## Calibration (after nozzle change)

Run in Console `PROBE_CALIBRATION`, the use a piece of paper to calibrate the offset.
Run `BED_SCREWS_ADJUST` after major movements of the printer.
Run `SAVE_CONFIG` to update printer.cfg with new valies.
