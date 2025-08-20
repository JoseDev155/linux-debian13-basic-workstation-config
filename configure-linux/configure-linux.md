# Configure Linux

## Post-installation

### Install Graphic Interface

To do a Gnome Minimal install (as root):

```bash
apt install gnome-core gdm3 -y
```

Start `gdm3` (as root):

```bash
systemctl start gdm
```

### Install and configuration of Timeshift

Install **Timeshift** (as root):

```bash
apt install timeshift -y
```

Then start **Timeshift**.

If you configure the `/root` partition with `btrfs` and then, you mount the partition in a subvolume:

* Select **BTRFS**
* Select the Snapshot location (the `/root` in this case)
* Select the levels (frequency) of Snapshot creation: **Monthly**, **Weekly**, **Daily**, **Hourly**, **Boot**

That´s all.

### What's Timeshit?

**Timeshift*** allows us move in time between Snapshots.

It doesn't create a backup or copy, it creates a reference of the changes made to the partition. The Snapshots are very light.

**Timeshift** works very similar to **Git**.