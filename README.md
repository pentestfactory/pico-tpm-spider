# pico-tpm-spider (Pre-compiled Firmware)

Pre-compiled UF2 firmware image for [decrazyo/pico-tpm-spider](https://github.com/decrazyo/pico-tpm-spider), a tool for extracting BitLocker Volume Master Keys (VMK) from discrete TPM 2.0 chips via SPI bus sniffing on the Raspberry Pi Pico. This repository provides the ready-to-flash firmware for security professionals who want to skip the build process.

## Flashing

1. Hold the **BOOTSEL** button on the Raspberry Pi Pico.
2. While holding BOOTSEL, connect the Pico via USB.
3. The Pico appears as a USB mass storage device (e.g. `RPI-RP2`).
4. Copy the firmware image to the device:

```
cp pico-tpm-spider.uf2 /media/$USER/RPI-RP2/
```

The Pico restarts automatically and runs the sniffer firmware.

## Requirements

- Raspberry Pi Pico H (pre-soldered headers recommended)
- IC hook clips (5-6 pieces)
- Dupont cables (female-to-female, 5 pieces)
- Micro-USB to USB-A cable
- Target system with a discrete SPI-based TPM 2.0

## Scope

This firmware targets discrete TPM chips communicating over SPI at clock rates between 10 and 50 MHz. It does not work against firmware-based TPMs (fTPM/Intel PTT), as these do not expose key material on an external bus.

## Bus Voltage

The Raspberry Pi Pico operates at 3.3V logic levels. Verify the target SPI bus voltage with a multimeter before connecting. Systems running at 1.8V (e.g. Dell Precision 3490) require a level shifter such as the TXS0108E.

## Disclaimer

This tool is intended for authorized security assessments and research purposes only. Unauthorized access to computer systems is illegal. Always obtain proper authorization before conducting any security testing.

## References

- [BitLocker TPM-Angriff: VMK per SPI-Sniffing auslesen (Pentest Factory Blog)](https://www.pentestfactory.de/bitlocker-tpm-angriff-vmk-per-spi-sniffing-auslesen/) -- Full writeup with step-by-step PoC on a Dell Latitude 7280
- [decrazyo/pico-tpm-spider](https://github.com/decrazyo/pico-tpm-spider) -- Original repository and source code
- [Bypassing BitLocker: Full Disk Decryption for less than $5](https://www.youtube.com/watch?v=...) -- D0zer & V00t, CypherCon 9.0
- [BitLocker Countermeasures (Microsoft)](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/countermeasures)

## License

This firmware is built from the original pico-tpm-spider source code. Refer to the [original repository](https://github.com/decrazyo/pico-tpm-spider) for license terms.
