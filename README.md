# Keychron K1 (V2)

## Keyboard shortcuts

This is a table of shortcuts for the Keychron K1.
Parentheses indicate that those keys should be pressed first, and then others in the shortcut. For example:

    ((fn) + l) + lightkey [6 seconds]

Means that the `fn` key should be pressed, then the `l` key, and then the `lightkey`.
The square brackets indicate how long the entire key combination should be pressed.

|              Shortcut             |                   Action                   |          Version          |
|-----------------------------------|--------------------------------------------|---------------------------|
| (fn) + 1                          | switch to bluetooth pairing 1              | *                         |
| (fn) + 2                          | switch to bluetooth pairing 2              | *                         |
| (fn) + 3                          | switch to bluetooth pairing 3              | *                         |
| (fn) + s + o [3 seconds]          | toggle auto sleep mode                     | *                         |
| (fn) + x + l [3 seconds]          | (WINDOWS MODE) swap multimedia and fn keys | *                         |
| (fn) + k + c [3 seconds]          | (MAC MODE) swap F5 and F6 to multimedia    | 2.6+                      |
| (fn) + left                       | cycle colours left                         | 2.7+                      |
| (fn) + right                      | cycle colours right                        | 2.7+                      |
| (fn) + lightkey                   | toggle keyboard lights                     | 2.7+                      |
| (fn) + capslock + p [6 seconds]   | toggle capslock independent of backlight   | 2.72+ buggy, good in 3.6+ |
| ((fn) + l) + lightkey [6 seconds] | toggle lock light effect                   | 3.6+                      |

## Toggle multimedia key state in Linux systems

You might find some success switching the `fnmode` toggle to `2` in the `hid_apple` driver.

```bash
echo 2 | sudo tee /sys/module/hid_apple/parameters/fnmode
```

Try a combination of that, and setting your keyboard to Windows mode and pressing the `(fn) + x + l` key combination.
How to persist these settings varies per system.

### Arch Linux

```bash
echo "options hid_apple fnmode=2" | sudo tee /etc/modprobe.d/hid_apple.conf
```

And then regenerate the ramdisk.

```
sudo mkinitcpio -P
```


### Debian based systems

Create the same file

```bash
echo "options hid_apple fnmode=2" | sudo tee /etc/modprobe.d/hid_apple.conf
```

And then regenerate the ramdisk.

```
sudo update-initramfs -u
```

## Other Resources

* https://github.com/Kurgol/keychron/blob/master/k2.md
* https://wiki.archlinux.org/index.php/Apple_Keyboard#Function_keys_do_not_work
* https://gitlab.com/keychron/k2/-/tree/master/Issues
* https://www.reddit.com/r/MechanicalKeyboards/comments/d5io49/keychron_k2_f_keys_dont_work_w_linux_help/
* https://gist.github.com/mid9commander/669273
* https://gist.github.com/j2ko/00254950a24498df5902ddc9fceb5ee0
* https://www.keychron.com/pages/firmware-for-k1-v2-v3-keyboards
