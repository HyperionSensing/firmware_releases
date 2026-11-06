# NimBLE-CDC dongle firmware

Firmware for the nRF52840 USB dongles (PCA10059) that the RF box production
tool uses as Bluetooth radios. Each release is published here by `mkrelease.sh`
in the firmware's source repo.

- `version.txt`: the latest release
- `blehci_cdc_dfu.zip`: the latest release's DFU package
- `blehci_cdc_dfu_<version>.zip`: every release's DFU package

To update every connected dongle, run `dfuAllConnected.sh` from the firmware's
source repo: it downloads the latest release from here, warns about any dongle
on another version, and flashes every dongle in DFU mode.

To flash one by hand, press the dongle's side button to put it in DFU mode,
then:

    nrfutil dfu usb-serial -pkg blehci_cdc_dfu.zip -p /dev/tty.usbmodem<SERIAL>1

A dongle reports its version in its USB product name, e.g. "NimBLE-CDC 1.01".
Versions before 1.01 report just "NimBLE-CDC".
