# Install Linux

## Installation

### Partitioning method

**NOTE**: We will use a 2 TB disk as an example.

* Manual

Partitioning table:

| Partition | Size   | File system              | Purpose               |
| --------- | ------ | ------------------------ | --------------------- |
| EFI       | 512 MB | System partition EFI     | Bootloader partition             |
| `/boot`   | 2 GB   | `ext4`                   | Kernel partition             |
| `swap`    | 33 GB  | `swap`                   | Recommended for hibernation `RAM + 1` |
| `/`       | 33 GB | `btrfs`                  | Root                  |
| `/home`   | 33 GB | `xfs`                    | User                  |
| `/var`    | 30 GB  | `xfs`                    | Logs, variable files, etc                   |
| `/tmp`    | 10 GB  | `ext4` or `tmpfs`                  | Temporary files                 |

* **Root** with `btrfs`: Allows you to have CoW (**Copy-on-Write**) file systems.
* **Home** with `xfs`: Allows you to have **Referenced Copy** (similar to CoW).

## Program selection

Choose the programs to install:

* [x] SSH server
* [x] Standard system utilities

## Renaming root

This step is because Debian doesn't configure well the `btrfs` to use tools like **Timeshift**.

See information about the disk storage and the partitioning and mounted file systems:

```bash
df -Th
```

The `btrfs` should be mounted on a sub volume that Timeshift expects.

Mounting on `/mnt`:

```bash
mount /dev/<btrfs-partition> /mnt
```

Moving to `/mnt`:

```bash
cd /mnt
```

Checking the content in the dir:

```bash
ls -l
```

Will see:

```plaintext
root @rootfs
```

Renaming `root`:

```bash
mv @rootfs/ @
```

### Editing the mounts file

Last changes:

```bash
cd /
```

Edit the mounts archive:

```bash
nano /etc/fstab
```

Renaming `@rootfs` to `@`:

```plaintext
UUID=<something> / btrfs defaults,subvol=@ 0 0
```

### Editing the GRUB

Moving to GRUB:

```bash
cd /boot/grub
```

Checking the content in the dir:

```bash
ls
```

Checking the content in `grub.cfg`:

```bash
nano grub.cfg
```

We need to correct the references to `@rootfs`. For that, we're going to use:

```bash
update-grub
```

**NOTE**: We´re going to install the Graphic Interface in `configure-linux.md`.

### References

* Link to the YouTube video: [Install Debian 13 Trixie for Workstation use](https://youtu.be/aiI_23UEIqc?si=YxHlmTN3sgihSR_s)