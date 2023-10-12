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

###  /dev
This directory contains special device files (also known as device nodes) which represent devices built into or connected to the system. These special files are essential for the system to function properly. Such device files represent character (byte-stream) and block I/O devices; network devices do not have device nodes in Linux, and are instead referenced by name, such as eth1 or wlan0.

All modern Linux distributions use the udev system, which creates nodes in the /dev directory only as needed when devices are found. If you were to look at the /dev directory on an unmounted filesystem, you would find it empty.

On ancient systems (or embedded devices), it can be created by MAKEDEV or mknod at install or at any other time, as needed.

### /etc
This directory contains machine-local configuration files and some startup scripts; there should be no executable binary programs. Files and directories which the FHS requires to be found in this directory include:

csh.login, exports, fstab, ftpusers, gateways, gettydefs, group, host.conf, hosts.allow, hosts.deny, hosts.equiv, hosts.lpd, inetd.conf, inittab, issue, ld.so.conf, motd, mtab, mtools.conf, networks, passwd, printcap, profile, protocols, resolv.conf, rpc, securetty, services, shells, syslog.conf.

### /home
On Linux systems, user directories are conventionally placed under /home
All personal configuration, data, and executable programs are placed in this directory hierarchy

### /lib and /lib64
These directories should contain only those libraries needed to execute the binaries in /bin and /sbin. These libraries are particularly important for booting the system and executing commands within the root filesystem.

Kernel modules (often device or filesystem drivers) are located under /lib/modules/<kernel-version-number>, as in /lib/modules/5.19.4.

PAM (Pluggable Authentication Modules) files are stored in distribution-dependent locations such as /lib64/security or /lib/x86_64-linux-gnu/security.

Systems which support both 32-bit and 64-bit binaries need to keep both kinds of libraries on the system. On some distributions, there are separate directories for 32-bit libraries (/lib) and 64-bit libraries (/lib64).

Command:

$ ls -l /lib* 

Output:

lrwxrwxrwx 1 root root 7 Apr 23 2020 /lib -> usr/lib
lrwxrwxrwx 1 root root 9 Apr 23 2020 /lib64 -> usr/lib64

### /media
This directory was typically used to mount filesystems on removable media. These include CDs, DVDs, and USB drives, and even Paleolithic era floppies.

Linux systems mount such media dynamically upon insertion, and udev creates directories and then mounts the removable filesystems there, with names that are set with udev rules specified in configuration files. Upon unmounting and removal, the directories used as mount points disappear.

### /mnt
This directory is provided so that the system administrator can temporarily mount a filesystem when needed. A common use is for network filesystems, including:

* NFS
* Samba
* CIFS
* AFS.

  Historically, /mnt was also used for the kinds of files which are now mounted under /media (or /run/media) in modern systems.

### /opt
This directory is designed for software packages that wish to keep all or most of their files in one isolated place, rather than scatter them all over the system in directories shared by other software

### /proc
This directory is the mount point for a pseudo-filesystem, where all information resides only in memory, not on disk. Like /dev, the /proc directory is empty on a non-running system.

### /sys
This directory is the mount point for the sysfs pseudo-filesystem where all information resides only in memory, not on disk. Like /dev and /proc, the /sys directory is empty on a non-running system. It contains information about devices and drivers, kernel modules, system configuration structures, etc.

sysfs is used both to gather information about the system

### /root
This directory (pronounced "slash-root") is the home directory for the root user.

### /sbin
This directory contains binaries essential for booting, restoring, recovering, and/or repairing in addition to those binaries in the /bin directory. They also must be able to mount other filesystems on /usr, /home and other locations if needed, once the root filesystem is known to be in good health during boot.

The following programs should be included in this directory (if their subsystems are installed):

fdisk, fsck, getty, halt, ifconfig, init, mkfs, mkswap, reboot, route, swapon, swapoff, update.

### /srv
According to the Filesystem Hierarchy Standard (FHS):

"/srv contains site-specific data which is served by this system.

This main purpose of specifying this is so that users may find the location of the data files for particular service, and so that services which require a single tree for readonly data, writable data and scripts (such as cgi scripts) can be reasonably placed.

### /tmp
This directory is used to store temporary files, and can be accessed by any user or application. However, the files on /tmp cannot be depended on to stay around for a long time.

### /usr
The /usr directory can be thought of as a secondary hierarchy. It is used for files which are not needed for system booting. Indeed, /usr need not reside in the same partition as the root directory, and can be shared among hosts using the same system architecture across a network.

### /var
This directory contains variable (or volatile) data files that change frequently during system operation. These include:
* Log files
* Spool directories and files
* Administrative data files
* Transient and temporary files, such as cache contents.

### /run
The purpose of /run is to store transient files: those that contain runtime information, which may need to be written early in system startup, and which do not need to be preserved when rebooting.

Generally, /run is implemented as an empty mount point, with a tmpfs ram disk (like /dev/shm) mounted there at runtime. Thus, this is a pseudo filesystem existing only in memory.

Some existing locations, such as /var/run and /var/lock, will be now just symbolic links to directories under /run. Other locations, depending on distribution taste, may also just point to locations under /run.
