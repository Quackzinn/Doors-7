# DOORS 7
**Windows 7, but Linux.**

Nowadays, Windows, and Microsoft in general, sucks.

Windows 7 was the **BEST OS EVER**, but it is old and unsafe.

So I had a simple question:

**Why don't we rebuild it, but make it modern?**

That's DOORS 7.



## What is DOORS 7?

DOORS 7 is an attempt to rebuild Windows 7 as a modern Linux operating system. The project is not focused on reproducing a few visual details or making an existing Linux desktop resemble Windows 7. The idea is to build the system itself around the Windows 7 experience, while replacing the underlying proprietary technology with Linux and open-source software.

That means the desktop, system utilities, file management, configuration tools, application integration, window management, notifications, search, and other parts of the operating system are considered part of the project rather than things that should simply be borrowed from an existing desktop environment. Linux is the foundation, but the user-facing system is being designed specifically for DOORS 7.

The project is intentionally being built from a low-level starting point. Instead of taking an existing desktop distribution and modifying it until it looks right, DOORS 7 starts with Linux From Scratch and builds the system upward. This gives the project direct control over the userspace, installed components, system configuration, boot process, kernel, and eventually the graphical stack.

The final result should feel like an operating system of its own.



## Current Development

DOORS 7 is currently based on **Linux From Scratch 13.1-systemd**. The LFS build has already been completed successfully and the resulting system was moved from the temporary build environment to a dedicated EXT4 partition. The system can now be entered through the DOORS chroot environment, which provides the development environment being used to finish the base system before its first physical boot.

The current machine uses a BIOS/Legacy boot configuration and an MBR partition table, so there is no EFI system partition involved in the current installation. The DOORS system lives on its own partition rather than sharing the host operating system's root filesystem. The existing host GRUB installation is intended to remain in control of the machine, with DOORS 7 being added as another boot entry instead of replacing the existing bootloader installation.

The Linux kernel has already reached the compilation stage. DOORS 7 currently uses **Linux 7.1.8**, which has been configured specifically for the development hardware and successfully compiled inside the DOORS environment. The configuration includes built-in support for the SATA/AHCI storage controller, Intel PIIX ATA support, EXT4, keyboard input, virtual terminals, and the virtual terminal console. The kernel build completed successfully and generated the `arch/x86/boot/bzImage` kernel image, with additional kernel modules being built alongside it.

The next part of the base-system work is therefore no longer kernel compilation. The kernel needs to be installed into the DOORS `/boot` directory, the filesystem configuration needs to be completed, and the existing GRUB installation needs to receive a DOORS entry pointing to the new kernel and the dedicated DOORS partition. After that, the most important milestone of the current stage is simple: boot the system.



## The System

The technical foundation of DOORS 7 is deliberately small at this stage. Linux From Scratch provides the base userspace, systemd handles system initialization and service management, the GNU toolchain provides the fundamental compilation and runtime environment, Bash provides the primary shell, and Linux provides the kernel. These components are not being treated as the final operating system. They are the foundation on which the actual DOORS environment will be built.

This distinction matters because DOORS 7 is not intended to be another Linux distribution that happens to ship a familiar desktop. The current LFS system is closer to the raw material of the project. The graphical environment, desktop shell, system utilities, applications, and Windows compatibility layer still need to be developed and integrated on top of it.

The kernel is responsible for the hardware-facing part of the system, including processor scheduling, memory management, storage, input devices, networking, drivers, filesystems, and the interfaces exposed to userspace. DOORS does not need to replace the Linux kernel simply because the project is trying to recreate Windows 7. Instead, the project can build its own userspace around the kernel and use Linux's hardware and process infrastructure as the low-level foundation.

That approach also keeps the project realistic. Reimplementing an entire operating system kernel, hardware abstraction layer, driver model, userspace API, desktop environment, and application ecosystem simultaneously would turn DOORS 7 into a completely different project. Linux already provides a mature kernel and hardware platform, allowing development to focus on the parts that actually define the DOORS experience.



## Building Windows 7 on Linux

The most important part of DOORS 7 is not the kernel. It is everything that sits above it.

A Windows 7-like desktop requires much more than a wallpaper, a taskbar, and a Start Menu. The desktop has to manage windows, applications, input, notifications, system settings, files, processes, and the relationship between all of these components. The interface also needs to behave consistently, because reproducing only the appearance of Windows 7 would miss a large part of what makes the operating system recognizable.

DOORS 7 therefore intends to develop its own desktop environment rather than simply installing an existing Linux desktop and applying a Windows 7 theme. The taskbar, Start Menu, desktop, window management, file management, system configuration, search, notifications, and other core desktop functionality are planned as components of the DOORS environment.

The same principle applies to system applications. A file manager should not exist merely because Linux needs one. It should be part of the DOORS desktop and follow the conventions established by the rest of the system. The same applies to system settings, utilities, text editing, media handling, file operations, and other applications that users interact with regularly.

This does not mean every component has to be written from scratch. Existing Linux and open-source technologies can be used where they make technical sense. The important distinction is that they are being integrated into a system designed around the DOORS 7 model rather than simply being installed unchanged and called the operating system.



## Windows Application Compatibility

Windows application compatibility is another major part of the project, but it is a separate problem from recreating the Windows 7 desktop.

A Windows program can depend on far more than a collection of documented Win32 functions. Real software can rely on documented APIs, undocumented APIs, particular Windows versions, bugs or quirks of specific releases, COM, the Registry, Windows services, drivers, DirectX, codecs, installers, Internet Explorer components, legacy 16-bit APIs, NTFS behavior, native system calls, anti-cheat systems, DRM, and many other implementation details.

Because of that, simply saying that DOORS 7 will “support Windows applications” is not technically meaningful enough. Compatibility has to be tested application by application and subsystem by subsystem.

The initial direction is to use established open-source compatibility technology such as Wine rather than attempting to recreate the entire Windows NT architecture. DOORS 7 can then build integration around that technology, test real Windows applications, identify compatibility problems, and decide which parts need additional work.

This also means that Windows compatibility will not be treated as something that automatically appears when the desktop is finished. It is its own engineering problem, with its own testing requirements and its own limitations.



## Development Roadmap

The immediate goal is to get the current LFS-based system to a real boot. That means finishing the kernel installation, configuring `/etc/fstab`, adding the DOORS entry to GRUB, and successfully reaching the DOORS userspace without relying on the host system's root filesystem.

After the first successful boot, development can move away from the current low-level installation work and toward making the system usable. Networking, audio, power management, user management, graphics, and the graphical session will become the foundation for the actual desktop.

From there, the project moves into the part that most people will recognize as DOORS 7: the desktop environment, taskbar, Start Menu, window management, file manager, system settings, notifications, search, and system utilities. Applications and Windows compatibility will then be integrated into that environment rather than treated as unrelated packages.

The first Alpha release will come only after the system can boot and provide a usable DOORS desktop. Beta and 1.0 releases will come later as compatibility, stability, hardware support, applications, and the overall Windows 7 experience are developed further.



## Philosophy

Keep it simple.

Keep it understandable.

Keep it ours.

DOORS 7 is not trying to make Windows 7 fashionable again.

It is trying to answer one question:

**What if Windows 7 was rebuilt today, with Linux underneath?**

That's the project.

## Contributing

DOORS 7 is currently a solo project, and there is a lot I still don't know.

If you have experience with Linux internals, operating system development, desktop environments, graphical stacks, system programming, Wine, Windows compatibility, C/C++, build systems, or low-level Linux development, your knowledge could make a real difference here.

You don't need to take over the project. Code contributions are welcome, but so are technical reviews, architecture discussions, bug reports, testing, documentation, and simply pointing out when I'm doing something completely insane.

If you know something that I don't, teach me.

If you see a better way to implement something, tell me.

If you want to build part of DOORS 7 with me, contribute.

DOORS 7 started with a simple question. I don't expect to have all the answers myself.

Pull requests, issues, technical discussions, and contributions are welcome.
