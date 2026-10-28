# FeviOS Lite

**A deliberately minimal Debian-based Linux live system for older PCs.**

FeviOS Lite is the lightweight edition of FeviOS, built from official Debian Stable (Trixie) packages and the standard Linux kernel. It uses Openbox, tint2 and a small set of desktop utilities rather than a full desktop environment.

## Target hardware

- HP 15-series laptop
- Intel Pentium 3825U-class processor
- 4 GB RAM
- 500 GB HDD
- 64-bit x86 PC

## Main goal

The initial performance target is **less than 500 MB RAM at idle after boot and login**. This is a target, not a verified guarantee. Actual memory use depends on the kernel, firmware, display driver, hardware, live-session services and how RAM is measured. We will measure it on real hardware before claiming success.

## Lightweight design

- Debian Trixie base and official Debian repositories
- Openbox window manager
- tint2 panel
- Rofi application launcher (Super + Space)
- PCManFM file manager (Super + E)
- LXTerminal (Super + T)
- NetworkManager and Wi-Fi support
- PulseAudio and basic ALSA tools
- zram swap support
- No compositor, desktop search indexer or dock
- APT package manager
- Firmware packages enabled for broad hardware support
- APT recommends disabled to reduce unnecessary packages

## Build using GitHub Actions

1. Open the [FeviOS Lite repository branch](https://github.com/Inexra/cloud-os-desktop/tree/fevios-lite).
2. Open **Actions**.
3. Select **Build FeviOS Lite ISO**.
4. Choose **Run workflow** on the `fevios-lite` branch.
5. Download the `FeviOS-Lite-ISO` artifact after a successful run.
6. Extract the ZIP to obtain the ISO.

If the build fails, download the `FeviOS-Lite-build-log` artifact and inspect the last error.

## Safe testing

- Keep Windows and the internal drive untouched.
- Use a separate USB drive for testing.
- Choose the live/try session and do not start an installer.
- Do not erase or repartition any disk.
- Back up important files before any future installation work.

## Applications

The first image prioritizes boot speed and low idle RAM. Large applications such as Chrome, VLC, Java, BlueJ, WordCraft and DeckCraft are intentionally not preinstalled in this minimal edition. They can be added in later optional editions or installed with APT when internet access and sufficient storage are available. Running browsers, Java IDEs and media editors will naturally use more RAM than the idle desktop.

## Roadmap

1. Produce a repeatable bootable ISO.
2. Test live boot, display, Wi-Fi, sound, touchpad and suspend on the HP laptop.
3. Measure idle RAM using `free -h` and `/usr/bin/time` where appropriate.
4. Tune startup services based on measured results.
5. Add an optional applications bundle without increasing the minimal image by default.
6. Consider an installer only after live USB testing is reliable.

FeviOS Lite is an early development project and is not yet certified for production use. Debian and other upstream projects retain their respective trademarks and licenses.
