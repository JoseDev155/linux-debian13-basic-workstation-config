# Compile Kernel in Linux

## Download the Kernel

* Kernel: x.y.z

## Install necessary libraries (from Debian)

In a terminal (as root):

```bash
apt install build-essential libncurses5-dev fakeroot libssl-dev gcc bc bison flex libelf-dev kmod cpio rsync python3 -y
```

## Unzip the Kernel

Use:

```bash
tar Jvxf linux-<version>.tar.xz 
```

## Copy the current Kernel configurations

Enter the unzip dir:

```bash
cd linux-<version>
```

Checking the content in the dir:

```bash
ls
```

Copy the current configurations for the modules to be configured:

```bash
cp /boot/config-<current-version>-amd64 ./.config
```

## Remove the Debug Information

Use:

```bash
nano .config
```

Change `y` for `n` in these lines:

```plaintext
CONFIG_DEBUG_INFO=n
...
CONFIG_DEBUG_INFO_BTF=n
```

## Make a Change in the Configuration:

Use:

```bash
make menuconfig
```

We add all options of NTFS, a file system that supports writing and reading:

```plaintext
File systems
    DOS/FAT/EXFAT/NT Filesystems
        ...
        <M> NTFS Read-Write File Systems support
        [*] 64 bits per NTFS clusters
        [*] activate support of external compressions lzx/xpress
        [*] NTFS POSIX Access Control Lists
```

## Number of cores

Use:

```bash
nproc
```

## Compiling the Kernel

Compiling with all cores and taking time:

```bash
time make -j<value-of-nproc>
```

Compiling the modules with all cores and taking time:

```bash
time make modules -j<value-of-nproc>
```

Sign the modules with all cores and taking time:

```bash
time make modules_install -j<value-of-nproc>
```

Install the kernel:

```bash
make install
```

Reboot the computer:

```bash
reboot
```

## Kernel Size

Generic command:

```bash
uname -a
```

Move to:

```bash
cd /lib/modules
```

Checking the content in the dir:

```bash
ls
```

Get size:

```bash
du -h <version>/
```

## References

* Link to the YouTube video: [Compile the Linux Kernel](https://youtu.be/GIXjZz57KDg?si=vSULF7S9z-iLhd7m)