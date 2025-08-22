# Error `apt update` in Linux

## Error in Debian 13

If we execute (as root)

```bash
apt update
```

It's because we have the previous repository format `sources.list`.

The original route:

```bash
nano -l -m /etc/apt/sources.list
```

* `-l`: list
* `-m`: mouse

We comment the CD/DVD repository:

```bash
# deb cdrom: ...
```

Copy the Debian 12 repository from this [GitHub repo](https://gist.github.com/hakerdefo/5e1f51fa93ff37871b9ff738b05ba30f), verify all
indexes in the repositories writing the FTP URL in the browser. Then, change `bookworm` for `trixie` and paste in the `sources.list`:

```bash
deb https://ftp.debian.org/debian/ trixie contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ trixie contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ trixie-updates contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ trixie-updates contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ trixie-proposed-updates contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ trixie-proposed-updates contrib main non-free non-free-firmware

deb https://ftp.debian.org/debian/ trixie-backports contrib main non-free non-free-firmware
# deb-src https://ftp.debian.org/debian/ trixie-backports contrib main non-free non-free-firmware

deb https://security.debian.org/debian-security/ trixie-security contrib main non-free non-free-firmware
# deb-src https://security.debian.org/debian-security/ trixie-security contrib main non-free non-free-firmware
```

In the case that it doesn't exist yet, Debian isn´t gpoing to read it, it's going to omit it.

The, we execute:

```bash
apt update
```

This isn´t going to give us any error because the **Distro Codename** also have a file:

```bash
cat /etc/lsb-release
```

Or:

```bash
cat /etc/os-release
```

Contains system information. Then the Distro aims to **Debian 13**:

```plaintext

```

For that, the key already exists in the system and we don´t need to sign or introduce the key.

## References

* Link to the YouTube video: [Repositories Solution Debian 13 TRIXIE](https://youtu.be/tqmZEsy8ayo?si=aXEbFmNVT3UYWT4p)