# Ender 3 Klipper
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
## SKR setup
Insert the SD to the SKR board. It will flash itself.

## Useful links:
- BLTouch on Klipper: https://www.youtube.com/watch?v=iEo7tJ0wbPU
- Klipper config reference: https://github.com/Klipper3d/klipper/blob/master/docs/Config_Reference.md
- ender3 example: https://github.com/Klipper3d/klipper/blob/5d0d6d5a32930a9daa249e20148457a754beaac3/config/printer-creality-ender3-2018.cfg#L1
- SKR-mini-E3-v2 example: https://github.com/Klipper3d/klipper/blob/dd03cca49b920762f959d8cce047a6cc4debf60b/config/generic-bigtreetech-skr-mini-e3-v2.0.cfg
