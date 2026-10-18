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

This is an early development build, not a finished or production-certified operating system. GitHub Actions builds a bootable ISO and publishes it as a workflow artifact. The image must be tested on real hardware before considering installation.

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

- Debian Stable base and XFCE desktop for modest hardware
- Dark, uncluttered desktop with a dock
- File manager, browser, terminal, settings and network controls
- Java 21 development tools and BlueJ IDE for Java coursework (included in the image)
- Cloud ISO builds using GitHub Actions
- No local Android Studio, Docker or Linux build environment required

## Java and BlueJ

The image build downloads the official BlueJ 6.0.1 Debian package from the BlueJ-Greenfoot GitHub release and includes it with OpenJDK 21 and OpenJFX. BlueJ is intended for 64-bit Intel/AMD systems. In the live session, look under **Applications → Development** or launch `bluej` from a terminal. A live session is temporary: files and installed changes may be lost on shutdown unless saved to another drive.

Official BlueJ site: https://bluej.org/

## Roadmap

1. Produce a repeatable bootable ISO.
2. Test boot, Wi-Fi, sound, touchpad, display and suspend on target hardware.
3. Refine the FeviOS theme, wallpaper, dock and app launcher.
4. Add a clear first-run setup and useful defaults.
5. Add installer support only after live-session testing is reliable.

FeviOS uses Debian and other open-source components. Their respective licenses and trademarks remain with their owners.
