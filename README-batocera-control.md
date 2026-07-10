# Batocera Control (patch 06)

Decky plugin (fork of [Armada Control](https://github.com/virtudude/armada)).

**Needs:** **04** (Decky), **12** (Power tab). With UFS layout also **01** (homebrew bind).

| Layout | Install |
|--------|---------|
| SD + UFS | `bash install.sh` (or `./apply-all.sh`) |
| SD only | `bash install-sd.sh` (or `./apply-sd-only.sh`) |

## Tabs

| Tab | What |
|-----|------|
| Compatibility | Per-game FEX profiles |
| Power | Eco / balanced / performance + fan |
| LEDs | Joystick rings (`batocera-led-handheld`) |
| OLED | Idle dim timing (normal = ES brightness) |
| Paddles | M1/M2 + combos (clicks, shortcuts, etc.) |
| Advanced | SSH, calibration |

## Install

```bash
cd /userdata/Batocera-Odin3-Patches/patches/06-armada-control
bash install.sh
```

Steam → Quick Access → **Batocera Control**

Log: `/userdata/system/logs/armada-control-install.log`

## Config paths

- Paddles: `/userdata/system/configs/batocera-control/back-paddles.json`
- Game tweaks: `/userdata/system/configs/batocera-control/game-tweaks.json`
- Power: `/userdata/system/configs/batocera-control/power-profiles.conf`

## Power LED

Keep the power-button LED off (optional):

```bash
cp leds.conf.example /userdata/system/configs/leds.conf
/etc/init.d/S51led-handheld restart
```
