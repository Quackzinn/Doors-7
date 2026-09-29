# DOORS 7

**Windows 7, but Linux.**

Windows, and Microsoft in general, sucks.
Windows 7 was the **BEST OS EVER**, but it is old and unsafe.

So I had a simple question:
**Why don't we rebuild it, but make it modern?**

That's DOORS 7.

The goal is to actually rebuild Windows 7 as a modern Linux operating system, recreating its desktop, system tools, applications, and overall experience while using Linux underneath.

## Current Status

DOORS 7 is currently being built from **Linux From Scratch 13.1-systemd**.

The LFS system has been successfully built and moved to its own dedicated partition. The DOORS chroot environment is working, and Linux 7.1.8 has been configured and compiled successfully.

### Current progress

* [x] Build Linux From Scratch 13.1-systemd
* [x] Move the system to a dedicated partition
* [x] Set up the DOORS chroot environment
* [x] Prepare Linux 7.1.8
* [x] Configure Linux 7.1.8
* [x] Compile Linux 7.1.8
* [ ] Install the kernel
* [ ] Configure the filesystem table
* [ ] Configure the bootloader
* [ ] Boot DOORS 7 for the first time
* [ ] Build the graphical environment
* [ ] Recreate the Windows 7 desktop
* [ ] First Alpha release

## What DOORS 7 Is Trying to Rebuild

The project is focused on recreating the parts of Windows 7 that make the system what it is, rather than simply copying its visual appearance.

Planned components include:

* Desktop environment
* Taskbar
* Start Menu
* Window management
* File Explorer
* Control Panel and system settings
* Notifications
* Search
* System tools
* Default applications
* Windows application compatibility

The implementation will use Linux and open-source components underneath instead of relying on the original Windows source code or proprietary Windows components.

## System

The current system is being built from the ground up using:

* Linux From Scratch 13.1-systemd
* Linux 7.1.8
* systemd
* GNU toolchain
* Bash

The goal is to have control over the entire system instead of starting with an existing desktop Linux distribution.

## Roadmap

### Core System

* [x] LFS system
* [x] Dedicated DOORS partition
* [x] DOORS chroot
* [x] Linux kernel configuration
* [x] Linux kernel compilation
* [ ] First successful boot
* [ ] Networking
* [ ] Audio
* [ ] Power management
* [ ] User management

### Windows 7 Desktop

* [ ] Desktop
* [ ] Taskbar
* [ ] Start Menu
* [ ] Window management
* [ ] File Explorer
* [ ] System settings
* [ ] Notifications
* [ ] Search
* [ ] System tools

### Applications

* [ ] File manager
* [ ] Text editor
* [ ] Image viewer
* [ ] Multimedia applications
* [ ] System utilities
* [ ] Default applications

### Windows Compatibility

* [ ] Wine integration
* [ ] Windows application testing
* [ ] Windows application integration

### Releases

* [ ] DOORS 7 Alpha
* [ ] DOORS 7 Beta
* [ ] DOORS 7 1.0

## License

DOORS 7 is licensed under the GNU General Public License v3.0.

See [LICENSE](LICENSE) for more information.
