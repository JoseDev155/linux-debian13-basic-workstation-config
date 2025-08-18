# Install NVIDIA Drivers in Linux

## Install NVIDIA Drivers in Debian 13

### Download NVIDIA Drivers

* Go to the [NVIDIA website](https://www.nvidia.com/en-us/drivers/).
* Search your driver in **Manual Driver Search**.
* Download the driver.

**TIP**: You can request your architecture with:

```bash
arch
```

### Install headers

Search our headers with:

```bash
sudo apt search linux-headers-amd64
```

Install:

```bash
sudo apt install linux-headers-amd64
```

### Install necessary libraries to compile de driver

In a terminal:

```bash
sudo apt install cmake make bison -y
```

Search the `build-essential` package:

```bash
apt search build-essential
```

Install:

```bash
sudo apt install build-essential
```

### Execute the driver

Move to:

```bash
cd Downloads/
```

Checking the content in the dir:

```bash
ls
```

We apply execution permissions to the driver:

```bash
chmod +x <nvidia-driver>.run
```

Exec the driver (as root):

```bash
./<nvidia-driver>.run
```

Choose **Continue installation**.

Reboot the computer (as root):

```bash
reboot
```

### Checking the driver installation:

In a terminal:

```bash
nvidia-smi
```

## References

* Link to the YouTube video: [NVIDIA Drivers In Debian 13 TRIXIE](https://youtu.be/wdlQegO9Sic?si=MeZ6qFFy4hERkUKQ)