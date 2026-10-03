# Cardenza support

Build with `idf.py -B build-cardenza -D CARDENZA=ON -D SDKCONFIG=sdkconfig.cardenza build` using ESP-IDF 5.5.1, after exporting the IDF environment. Clone with git clone --recursive.

This port is based on upstream main `1b7930ea93dcc63a12a40ac6f418fbea87f8c065`. Original hardware targets remain available.

Hardware: original Cardputer V1 keyboard, 240x135 display and SPI SD; ES8156 DAC at I2C0x08 (SDA2/SCL1), stereo Philips I2S BCLK41/LRCK43/DOUT42; PDM microphone CLK43/DATA46. Keyboard LED EN21 is held high (off), and backlight uses GPIO38. No battery ADC, gyro, onboard RGB or PSRAM is assumed. The target checks codec identity before setup.

The original V1 matrix is selected explicitly. PDM microphone CLK43/DATA46 is retained; this tuner does not implement DAC playback. The q and q-infra submodules are pinned to 3048b9e489135ec13fd2b3fb3f80b3ae755fbdda and ecd71d47f3c47368d4d51cecd2ebae48a4843e0e, respectively.

Install only the application image through Software Launcher. Do not flash generated bootloader, partition table, merged images or erase the shared NVS. This target uses the Launcher's existing partition layout; a generated project partition table is only for local build sizing.

Upstream GPL-3.0-or-later notices in pitch detector sources remain unchanged. q and the vendored HAL retain their separate MIT licenses. No replacement application license is imposed.

A successful build is not a hardware test. These refreshed images require physical display, keyboard, audio/microphone and storage checks before claiming functional validation.
