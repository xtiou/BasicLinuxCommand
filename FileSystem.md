# FHS Linux Standard Directory Tree
## DIRECTORY	PURPOSE
* /	Primary directory of the entire filesystem hierarchy
* /bin	Essential executable programs that must be available in single user mode
* /boot	Files needed to boot the system, such as the kernel, initrd or initramfs images, and boot configuration files and bootloader programs
* /dev	Device Nodes, used to interact with hardware and software devices
* /etc	System-wide configuration files
* /home	User home directories, including personal settings, files, etc.
* /lib	Libraries required by executable binaries in /bin and /sbin
* /lib64	64-bit libraries required by executable binaries in /bin and /sbin, for systems which can run both 32-bit and 64-bit programs
* /media	Mount points for removable media such as CDs, DVDs, USB sticks, etc.
* /mnt	Temporarily mounted filesystems
* /opt	Optional application software packages
* /proc	Virtual pseudo-filesystem giving information about the system and processes running on it. Can be used to alter system parameters.
* /run	Run-time variable data, containing information describing the system since it was booted. Replaces the older /var/run
* /sys	Virtual pseudo-filesystem giving information about the system and processes running on it. Can be used to alter system parameters. Similar to a device tree and is part of the Unified Device Model.
* /root	Home directory for the root user
* /sbin	Essential system binaries
* /srv	Site-specific data served up by the system. Seldom used.
* /tmp	Temporary files; on many distributions lost across a reboot and may be a ramdisk in memory.
* /usr	Multi-user applications, utilities and data; theoretically read-only.
* /var	Variable data that changes during system operation

### additional distribution-specific :
* /misc, which can be used for miscellaneous data
* /tftpboot, which is used for booting using tftp
 
### the root (/) directory
the root partition must contain all essential files required to boot the system and then mount all other file systems.
Thus, it needs utilities, configuration files, boot loader information, and other essential startup data.
It must be adequate to:

* Boot the system.​
* Restore the system from system backups on external media such as tapes and other removable media or NAS etc.​
* Recover and/or repair the system; an experienced maintainer must have the tools to diagnose and reconstruct a damaged system.

### /bin
The /bin directory:

* It contains executable programs and scripts needed by both system administrators and unprivileged users, which are required when no other filesystems have yet been mounted; for example, when booting into single user or recovery mode.
* may also contain executables which are used indirectly by scripts.
* may not include any subdirectories.

Required programs which must exist in the /bin/ directory include:

cat, chgrp, chmod, chown, cp, date, dd, df, dmesg, echo, false, hostname, kill, ln, login, ls, mkdir, mknod, more, mount, mv, ps, pwd, rm, rmdir, sed, sh, stty, su, sync, true, umount and uname

### /boot
The /boot directory contains everything required for the boot process. The two files which are absolutely essential are:
* vmlinuz: The compressed Linux kernel
* initramfs: The initial RAM filesystem, which is mounted before the real root filesystem becomes available

The /boot directory stores data used before the kernel begins executing user-mode programs. It also includes two files used for information and debugging:

* config : Used to configure the kernel compilation.
* System.map : Kernel symbol table, used for debugging.
 
  
