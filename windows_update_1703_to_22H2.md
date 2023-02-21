I recently had to update a Windows 10, from version `1703` to version `22H2` and things were harder than they could have been...

Here, I simply list the 3 main problems I encountered and the corresponding fixes. You might not encounter similar issues, and I can't garantee that these fixes will work for you, but they might be a first investigation step.

- [Error 0x80070070](#error-0x80070070----not-enough-disk-space)
- [Error 0xc1900201](#error-0xc1900201----you-cant-install-windows-on-a-usb-flash-drive-using-setup)
- [Realtek Bluetooth](#realtek-bluetooth-your-pc-has-a-driver-or-service-that-isnt-ready-for-this-version-of-windows-10.-a-new-version-is-available)

🙏 I hope this helps 🙏

## Error 0x80070070 -- Not enough disk space

1) This one might seem stupid, but while the utility asked for `11Go` of free space, it actually took close to `30Go` when I finally managed to install the update. This is why you can encounter this error even though the utility thinks you have enough free space.

    **Fix:** Free around `30Go`.

2) If you use an external drive as free space, be sure that the first partition Windows will find has those `30Go` of free space. I'll illustrate this:
```
# Wrong
├─Local Disk (C:)  # 2Go free
├─External Drive Part 1 (D:)  # 150Mo free
└─External Drive Part 2 (E:)  # 30Go free

# Right
├─Local Disk (C:)  # 2Go free
├─External Drive Part 1 (D:)  # 30Go free
└─External Drive Part 2 (E:)  # whatever...

```

## Error 0xc1900201 -- You can't install Windows on a USB flash drive using Setup

**Fix:**
1) In the `Start > Settings > Update & security` menu, use the `Run the troubleshooter` button,
2) In `regedit`, set the value of `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control` to `0`, instead of `1`. Then reboot.

Reference [here](https://answers.microsoft.com/en-us/windows/forum/all/you-cant-install-windows-on-a-usb-flash-drive/003a982e-aa32-49ad-8bf5-e7e83d488c63).

## Realtek Bluetooth: Your PC has a driver or service that isn't ready for this version of windows 10. A new version is available

**Fix :** Simply follow [this](https://support.microsoft.com/en-us/topic/updating-to-a-new-version-of-windows-10-on-devices-with-some-driver-versions-for-realtek-bluetooth-radios-059c426a-755f-b88c-5c34-e0d1ecccf9c1) tutorial.
