# OpenIPC Wiki
[Table of Content](../README.md)

## TP-Link Tapo C110 (v?)
### GPIO
IRLed | WhiteLed | RedLed | GreenLed | Speaker | Reset | IRCut
-|-|-|-|-|-|-
GPIO14 | GPIO15 | GPIO46 | GPIO47 | GPIO61 | GPIO66 | GPIO78

```
cli -s .nightMode.irCutPin1 78
cli -s .nightMode.backlightPin 14
cli -s .audio.speakerPin 61
```

### Wireless
```
fw_setenv wlandev ssw101b-ssc333-tapo-c110
fw_setenv wlanssid Router
fw_setenv wlanpass 12345678
```

## TP-Link Tapo C110 (v2.26)
### Notes
 - Test point 501 is missing its bridge and pull-up resistor. You must bridge R504 to make TP501 usable. I was able to use snander and access the UART with the builtin pull-ups so R506 can be ignored.
 - The wireless chip is now a AltoBeam 6012b. You will need to make a [custom build](https://github.com/OpenIPC/builder) with `ssc333_lite_tp-link-tapo-c110-v26` for WiFi on the 8M flash.
### Test Points
TP501 | TP502 | TP503 | TP504
-|-|-|-|
UART:TX | UART:RX  | GND | Vcc (3.3v) |
I2C:SDA | I2C:CLK  | GND | Vcc (3.3v) |


### Wireless
```
fw_setenv wlandev atbm6012b-ssc333-tapo-c110
fw_setenv wlanssid Router
fw_setenv wlanpass 12345678
```
