# FeviOS

**A lightweight, macOS-inspired Linux desktop for older laptops.**

FeviOS is a community-built Debian Live image customized with XFCE, a dock, a simple dark theme and practical desktop applications. The first milestone is a bootable ISO that can be tested without installing or modifying Windows.

## Target hardware

- HP 15-series laptop
- Intel Pentium 3825U-class processor
- 4 GB RAM
- 500 GB HDD
- 64-bit x86 PC (confirm your exact CPU model before installing)

## Current status

This is an early development build, not a finished or production-certified operating system. The desktop is being tuned for low idle memory use with a target below 1 GB after login, but this is a goal rather than a verified guarantee until measured on the laptop. GitHub Actions builds a bootable ISO and publishes it as a workflow artifact. The image must be tested on real hardware before considering installation.

## Build FeviOS

1. Open the **Actions** tab in this repository.
2. Select **Build FeviOS ISO**.
3. Select **Run workflow** and run it on the `main` branch.
4. When the workflow completes, open the run and download the `FeviOS-ISO` artifact.
5. Extract the artifact ZIP to get the ISO file.

The workflow also runs after relevant project files are pushed.

## Safe testing

- Keep your existing Windows installation and files untouched.
- First test the ISO in a virtual machine if possible.
- To test on the laptop, use a separate USB drive and choose a one-time boot option only if you are comfortable doing so. No BIOS changes are part of this development step.
- Choose a **live / try** session and do not start the installer.
- Never select disk erase, repartition or install options until you have a verified backup and have deliberately decided to install FeviOS.

A live image is designed to run without modifying the internal drive, but booting from external media still requires care. Back up important files before any future disk or installation work.

## Design goals

- Debian Stable base and a trimmed XFCE desktop for modest hardware
- Low-overhead compositor settings, dock icon-zoom animation and zram swap tuning
- Target idle desktop RAM below 1 GB, subject to real-hardware testing
- Dark, uncluttered desktop with a dock
- Google Chrome as the default browser, plus VLC media player for video and audio
- File manager, terminal, settings and network controls
- Java 21 development tools and BlueJ IDE for Java coursework
- WordCraft word processor and DeckCraft presentation editor (included in the image)
- Cloud ISO builds using GitHub Actions
- No local Android Studio, Docker or Linux build environment required

## Browser and media player

The image downloads the official 64-bit Google Chrome Stable Debian package from Google's download server and sets Chrome as the default browser for newly created live-session users. Firefox is not installed by default. Chrome is proprietary software and its package increases the download and ISO size; its upstream package may add Google's update repository during installation. VLC is installed from Debian's repositories for local video and audio playback. Chrome can use substantial RAM on a 4 GB laptop, especially with many tabs, so keep tabs limited when prioritizing responsiveness.

Official Chrome download: https://www.google.com/chrome/

## Java and BlueJ

The image build downloads the official BlueJ 6.0.1 Debian package from the BlueJ-Greenfoot GitHub release and includes it with OpenJDK 21 and OpenJFX. BlueJ is intended for 64-bit Intel/AMD systems. In the live session, look under **Applications → Development** or launch `bluej` from a terminal. A live session is temporary: files and installed changes may be lost on shutdown unless saved to another drive.

Official BlueJ site: https://bluej.org/

## WordCraft and DeckCraft

FeviOS also downloads the x86-64 Debian packages for [WordCraft](https://github.com/storytold/wordcraft/releases/tag/v0.8.0), an open-source word processor for documents, and [DeckCraft](https://github.com/storytold/deckcraft/releases/tag/v0.8.0), an open-source presentation editor. Launch them from the Applications menu or search for their names. They are actively developed software, so check the release notes and keep backups of important work. The two installers add roughly 180 MB before ISO compression, so the final ISO will be larger.

## Performance targets

- Removed the broad `xfce4-goodies` metapackage to avoid installing unnecessary plugins and utilities.
- Kept XFCE's built-in compositor rather than adding another animation compositor, with window shadows disabled to reduce extra drawing.
- Configured Plank dock icon zoom for a restrained animated effect.
- Added zram swap tooling to help the 4 GB laptop cope with memory pressure. Compression uses CPU time, so performance must be checked on the actual machine.
- The target is less than 1 GB RAM at an idle desktop after login, with no browser, BlueJ, WordCraft or DeckCraft windows open. This cannot be promised from configuration alone: RAM readings vary by hardware, drivers, live-session cache and the measurement method.

## Roadmap

1. Produce a repeatable bootable ISO.
2. Test boot, Wi-Fi, sound, touchpad, display and suspend on target hardware.
3. Refine the FeviOS theme, wallpaper, dock and app launcher.
4. Add a clear first-run setup and useful defaults.
5. Add installer support only after live-session testing is reliable.

FeviOS uses Debian and other open-source components. Their respective licenses and trademarks remain with their owners.
