# Batocera Odin 3 — Community Patches (Generated With the 'priceless' power of Cursor)

Patches for **AYN Odin 3** on Batocera ARM (`44-dev-community`, July 2026).

For using with suckbluefrog custom build -> https://github.com/suckbluefrog/Batocera-Custom-Arm-Builds

Don't try to install **Batocera Control** Decky Plugin on a different Linux distribution, as **it won't work** (it includes invoke-commands exclusive to Batocera).


---

## Install

```bash
scp -r Batocera-Odin3-Patches root@batocera.local:/userdata/
ssh root@batocera.local
cd /userdata/Batocera-Odin3-Patches
chmod +x apply-all.sh apply-sd-only.sh patches/*/install.sh patches/*/install-sd.sh
./apply-all.sh      # SD + UFS (Steam/Wine on internal)
# ./apply-sd-only.sh  # SD only — see below
reboot
```

SSH: `root@batocera.local` / `linux`  
First install of **Batocera Control** needs network (git + npm).

After reboot: **Steam → Quick Access (Home + B) → Batocera Control**.

---

## Storage layout

| Layout | Script |
|--------|--------|
| **SD + UFS** — ROMs on SD, Steam/Wine/Decky on internal | `./apply-all.sh` |
| **SD only** — everything on microSD, no UFS | `./apply-sd-only.sh` |

Details: [STORAGE-MICROSD-vs-INTERNAL.md](STORAGE-MICROSD-vs-INTERNAL.md)

---

## Patches

| # | Folder | Purpose |
|---|--------|---------|
| 01 | `01-ufs-bind-mounts` | UFS mount + binds (Steam, Wine, Decky, PC games) |
| 02 | `02-back-paddles-gpio` | M1/M2 paddles |
| 04 | `04-decky-loader` | Decky PluginLoader |
| 05 | `05-yuzu-wayland-fix` | Yuzu on Wayland |
| 06 | `06-armada-control` | **Batocera Control** (needs **12** for Power tab) |
| 07 | `07-launch-freeze-fix` | Tools launch fix (`global.gamescope=0`) |
| 08 | `08-ui-scale-sway` | ES scale + Tools Configure zoom |
| 09 | `09-decky-lsfg` | LSFG-VK plugin |
| 10 | `10-suspend-resume-fix` | Suspend/resume recovery |
| 11 | `11-oled-care` | OLED idle dim (keeps your ES brightness) |
| 12 | `12-power-daemon` | Power profiles + fan |

One patch only: `bash patches/06-armada-control/install.sh`

---

## Batocera Control (06)

Decky plugin: game FEX profiles, power/fan, LEDs, OLED idle settings, M1/M2 remapping.

Details: [patches/06-armada-control/README.md](patches/06-armada-control/README.md)

---

## Update

```bash
scp -r Batocera-Odin3-Patches root@batocera.local:/userdata/
ssh root@batocera.local 'cd /userdata/Batocera-Odin3-Patches && ./apply-all.sh'
```

---

## Troubleshooting

| Issue | Try |
|-------|-----|
| PC games missing | Re-run patch **01**, `mount \| grep windows` |
| Steam stuck / won't start | `display.scale=1.0`, `steam.gamescope=1` |
| Tools Configure closes instantly | Re-run patch **08** |
| Control stuck on Loading | Re-run **06** + **12** |
| Power tab empty | Install **12**, then **06** |
| M1/M2 settings don't stick | Re-run **06** |
| OLED stuck dim | `batocera-brightness $(batocera-settings-get display.brightness)` |
| Freeze after sleep | See [SUSPEND-DEEP-SLEEP-INVESTIGATION.md](SUSPEND-DEEP-SLEEP-INVESTIGATION.md) |
| No built-in gyro | See [GYRO-MOTION-CONTROLS.md](GYRO-MOTION-CONTROLS.md) |

Logs: `/userdata/system/logs/decky-loader.log`, `odin-oled-care.log`, `odin-resume-fix.log`

---

## More docs

- [STORAGE-MICROSD-vs-INTERNAL.md](STORAGE-MICROSD-vs-INTERNAL.md) — SD+UFS vs SD-only
- [OLED-CARE.md](OLED-CARE.md) — patch 11 behaviour

---

## Credits

[Batocera](https://batocera.org) · [Armada Control](https://github.com/virtudude/armada) · [LSFG-VK](https://github.com/PancakeTAS/lsfg-vk)
