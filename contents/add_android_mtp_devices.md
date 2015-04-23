# Add Android MTP Devices

## Ubuntu 14.04

目前是靠 udev 把 MTP device 掛起來。不會自動被掛起來的 device，是因為 udev 不認識。編輯設定檔 `/lib/udev/rules.d/69-libmtp.rules`，照本宣科把 device 的 VID、PID 填入即可。