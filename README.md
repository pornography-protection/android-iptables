# Main steps as follows:

You need to install [LineageOS](https://lineageos.org/)

```
# Step 1: Create the file:
vim /system/etc/init/myboot.rc

# The file should contain the following two lines:
on boot
    exec u:r:su:s0 root root -- /system/etc/myboot.sh

# Change its mode to:
chmod 0755 /system/etc/init/myboot.rc
ls -a1l /system/etc/init/myboot.rc
# -rwxr-xr-x 1 root root 63 2021-11-21 16:43 /system/etc/init/myboot.rc

# Step 2: Create the file:
vim /system/etc/myboot.sh
chmod 755 /system/etc/myboot.sh
ls -a1l /system/etc/myboot.sh
# -rwxr-xr-x 1 root root 38246 2021-11-21 19:03 /system/etc/myboot.sh

# Contains:
#!/system/bin/sh

/system/bin/iptables -A OUTPUT -m owner --uid-owner 10195 -m string --string "xxx" --algo kmp -j REJECT
```
