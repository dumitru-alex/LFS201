Overview of [LHS](Linux File Hierarchy Structure.md)
## Notes:
- Two files which are absolutely essential to be in `/boot` are:
    - vmlinuz - the compressed Linux kernel
    - initramfs - the initial RAM filesystem, which is mounted before the real root filesystem becomes available. This file could also be called _initrd_ (initial RAM disk - older method)
- other files in `/boot`:
    - config - configuration file used when compiling the kernel
    - System.map - the kernel symbol table, which is very useful for debugging. It givs the hex addresses of all kernel symbols
- Libraries `/lib` and `/lib64` are particularly important for booting the system and executing commands within the root filesystem. Kernel modules (often device or filesystem drivers) are located under `/lib/modules/<kernel-version-number>`
- PAM (Pluggable Authentication Modules) files are stored in `/lib/security`
- the entries in `/proc` are often called **virtual files**
- important pseudo-files that provide up-to-the-moment glimpse of the system's hardware:
    - `/proc/interrupts`
    - `/proc/meminfo`
    - `/proc/mounts`
    - `/proc/partitions`
- other pseudo-files that provide system configuration information and interfaces:
    - `/proc/filesystems`
    - `/proc/sys`
- `sysfs`, which is the pseudo-filesystem mounted on `/sys` mount point, is used both to gather information about the system, and modify its behaviour while running.
- `/var` contains variable (volatile) data files that change frequently during system operation. For example:
    - log files
    - spool directories and files for printing, mail queues, etc.
    - administrative data files
    - transient and temporary files, such as cache contents
- `/var` cannot be mounted as read-only filesystem (obviously), but for security reasons, it's often considered a good idea to mount it as a separate filesystem. Furthermore, if the directory gets filled up, it should not lock up the system
- `/var/log` directory is where most of the log files are located, and `/var/spool` is where local files for processes such as mail, printing, and cron jobs are stored while awaiting action.
- A closer look at some of the subdirs of `/var`:
    - /var/ftp      -  ftp server base
    - /var/lib      -  persistent data modified by programs as they run
    - /var/lock     -  lock files used to control simultaneous access to resources
    - /var/log      -  log files
    - /var/mail     -  user mailboxes
    - /var/run      -  information about running system since the last boot
    - /var/spool    -  tasks spooled or waiting to be processed
    - /var/tmp      -  temporary files to be preserved across system reboot (sometimes linked to /tmp)
    - /var/www      - root for website hierarchies
    
     