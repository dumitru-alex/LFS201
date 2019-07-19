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