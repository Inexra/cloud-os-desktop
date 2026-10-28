# FeviOS Lite

**A lightweight Debian-based Linux desktop with a custom modern look.**

FeviOS Lite is built from official Debian Trixie packages and the standard Linux kernel. It deliberately avoids XFCE and other full desktop environments. The desktop uses Openbox, tint2, Rofi and PCManFM with a custom vector wallpaper, dark GTK settings, Papirus icons and a low-cost Picom compositor.

## Design goals

- Dark navy and blue-violet visual identity with custom SVG wallpaper
- Slim translucent-looking bottom dock/taskbar
- Rofi application launcher (Super + Space) with icons and fuzzy search
- Subtle window shadows and short fade transitions via Picom
- Keyboard shortcuts and clean dark GTK application styling
- No XFCE, GNOME, KDE or heavy desktop environment
- No blur effects, desktop search indexing or heavyweight dock

The compositor is intentionally configured with the XRender backend for older integrated graphics. If Picom causes tearing or uses too much memory on the target laptop, it can be disabled while keeping the rest of the visual theme.

## Target hardware

- HP 15-series laptop, Intel Pentium 3825U-class processor
- 4 GB RAM, 500 GB HDD
- 64-bit x86 PC

## Performance target

The goal is **less than 500 MB RAM at idle after boot and login**. This has to be verified on the actual laptop and is not guaranteed by the configuration alone. The compositor, display driver, firmware and live-session services all affect memory usage.

## Build using GitHub Actions

1. Open the [FeviOS Lite branch](https://github.com/Inexra/cloud-os-desktop/tree/fevios-lite).
2. Open **Actions** and choose **Build FeviOS Lite ISO**.
3. Run the workflow on branch `fevios-lite`.
4. Download the `FeviOS-Lite-ISO` artifact after a successful build.
5. Extract the ZIP to obtain the ISO.

If the build fails, download the `FeviOS-Lite-build-log` artifact and inspect the last error.

## Keyboard shortcuts

- **Super + Space:** app launcher
- **Super + E:** file manager
- **Super + T:** terminal
- **Super + R:** run command
- **Super + D:** show desktop
- **Alt + F4:** close focused window

## Safe testing

Use a separate USB drive and boot the live session without starting an installer. Keep Windows and the internal drive untouched. Back up important files before any future installation.

## Applications

This edition prioritizes a light base. Chrome, VLC, Java/BlueJ, WordCraft, DeckCraft and other large applications are not preinstalled. They can be added as optional packages after the base image boots reliably. Browser and IDE usage will require more RAM than the idle desktop.

## Roadmap

1. Build and validate a bootable ISO.
2. Test display, Wi-Fi, sound, touchpad and suspend on the HP laptop.
3. Measure idle RAM with `free -h`.
4. Compare memory with Picom enabled and disabled.
5. Tune startup services from real measurements.
6. Add optional software bundles and consider an installer after live testing.

FeviOS Lite is an early development project and is not yet certified for production use. Debian and upstream projects retain their respective trademarks and licenses.
