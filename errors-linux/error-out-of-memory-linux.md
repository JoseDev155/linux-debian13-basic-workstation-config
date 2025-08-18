# "Error: Out of memory" in Linux

This error appears when Linux start.

## Fixing error

Edit this file (as root):

```bash
nano /etc/default/grub
```

Change the next values:

```plaintext
```

Save the changes and update de GRUB (as root too):

```bash
update-grub
```

And then, restart the computer:

```bash
reboot
```