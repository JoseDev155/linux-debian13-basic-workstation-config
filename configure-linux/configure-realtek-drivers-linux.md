# Install Realtek Drivers in Linux

First, do the changes in `errors-linux/error-apt-update-linux.md` to access third party repositories.

## Install Realtek Drivers in Debian 13

### Linux headers

Search the meta-package:

```bash
apt search linux-headers-amd64
```

Install:

```bash
apt install linux-headers-amd64
```

### Difference between a Firmware and a Driver

The **Driver** brings advanced features and the **Firmware** is its purest state in the use of the system.

### Fimware

Search:

```bash
apt search firmware-misc-nonfree
```

Install:

```bash
apt install firmware-misc-nonfree
```

### Firmware Realtek

```bash
apt search firmware-realtek
```

Install:

```bash
apt install firmware-realtek
```

Then, reboot the system (as root):

```bash
reboot
```

## References

* Link to the YouTube video: [Drivers Realtek In Debian 13 TRIXIE](https://youtu.be/iOmLOyBO9EQ?si=AJ7JJAeLuk6PRb6o)