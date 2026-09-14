# rpi-i2s-dac-adc

ALSA SoC kernel module and Device Tree overlay for a Raspberry Pi I2S bidirectional
audio setup (PCM5102A DAC + digital microphone codec).

## Requirements

- Raspberry Pi with I2S support
- Matching kernel headers/build tree for your running kernel
- `make` and `dtc` (Device Tree Compiler)
- Root privileges for install/uninstall steps

## Build

From the repository root:

```bash
make
```

## Install

```bash
sudo make install
```

By default, `make install` copies:

- Kernel module: `/lib/modules/$(uname -r)/kernel/sound/drivers/rpi-i2s-dac-adc.ko`
- Overlay: `/boot/overlays/rpi-i2s-dac-adc.dtbo`

If your distribution uses a different boot mount point (for example
`/boot/firmware`), adjust the Makefile install path accordingly.

## Enable the overlay

Add the following line to your boot config file (typically
`/boot/config.txt`, or `/boot/firmware/config.txt` on some distributions):

```ini
dtoverlay=rpi-i2s-dac-adc
```

Reboot after changing `config.txt`.

## Load module

```bash
sudo modprobe rpi-i2s-dac-adc
```

## Uninstall

```bash
sudo make uninstall
```