 ## Processes - General Info
- every process has a: PID, PPID and PGID (process group ID)
- in addition, they have program code, data, variables, file descriptors and an environment
- the first **user process** on the system is the **init** which has a `PID = 1`. It is started as soon as the kernel is initialized and has mounted the root filesystem
    - exceptions are those processes initiated directly from the kernel (shows up with [] around their name in `ps` output) 
- **init** will run util the system is shut down; it will be the last user process to be terminated at that point. It serves as the ancestral parent of all other user processes, both directly and indirectly.
- if the parent process dies before child, the `ppid` of the child is set to **1** (the process is adopted by **init**)
> in recent Linux systems, using `systemd`, the ppid with be set to 2, which corresponds to an internal kernel thread known as **kthreadd**, which has taken the role of adopter from **init**.
- a child process which terminates before its parent, which has not waited for it and examined its exit code, is known as a **zombie** process. They have released almost all resources and remain only to convey their exit status. One function of the **init** process is to check on its adopted children and let those who have terminated die gracefully. Hence, it is sometimes known as the **zombie killer**, or more grimly, the **child reaper**.
- processes are controlled by **scheduling**, which is completely preemptive. Only the kernel has the right to preempt a process; they cannot do it to each other.
- for historical reasons, the largest PID has been limited to a 16-bit number, or 32768. It is possible to alter this value by changing `/proc/sys/kernel/pid_max`, since it may be inadequate for larger servers. As processes are created, eventually they will read `pid_max`, at which point they will start again at PID = 300.