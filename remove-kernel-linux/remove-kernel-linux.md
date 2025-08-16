# Remove Kernel in Linux

## Kernel information

First, update repositories to have the latest kernel version available:

```bash
sudo apt update
```

Get information with:

```bash
fastfetch
```

Or with the generic command:

```bash
uname -a
```

We can also open the **File Manager** and go to **File System**, `/usr/src/`. We see the diferent kernels in our computer.

We can also request with:

```bash
dpkg --get-selections | grep linux-image
```

## Delete Kernel

In a terminal:

```bash
sudo apt remove --purge <kernel-to-remove>
```

## Update Kernel information

Update the new configuration in our system:

```bash
sudo update-grub
```

## References

* Link to the YouTube video: [Remove Old Kernels in Linux](https://youtu.be/DFixlvRCEOY?si=eye1nM0XzcmOnEJ0)