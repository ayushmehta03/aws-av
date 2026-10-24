# Folder Structure for Linux Architecture

## 1. Understanding the Prompt

```text
root@ubuntu-dev:/#
```

- `root` = user
- `ubuntu-dev` = hostname
- `/` = current path

On EC2, there is no direct permission for root.

## 2. Important Directories

| Directory | Description |
|---|---|
| `/sbin` | System binaries (`/usr/sbin`). Used to manage the system, mostly for administration purposes. |
| `/lib` | Libraries used by the kernel (`/usr/lib`). |
| `/boot` | Supports starting and restarting the machine. Visible on EC2 machines. |
| `/bin` | User-related binaries and executables. Usually given permission to non-admin users too. |
| `/srv` | Holds data for services such as web servers. |
| `/var` | Stores logs, caches, and temporary files that change frequently. |
| `/etc` | Stores system configuration files. |

Both `/bin` and `/sbin` belong to `/usr`.

| Directory | Description |
|---|---|
| `/tmp` | Temporary files, cleared on reboot. |
| `/run` | Holds runtime data for processes. |
| `/proc` | Virtual file system for process and system information. |
| `/sys` | Virtual file system for hardware and kernel information. |
| `/dev` | Contains device files. |
| `/mnt` | Temporary mount point for external file systems. |
| `/data` | Likely your mounted volume. |