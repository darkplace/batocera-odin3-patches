# OLED care (patch 11)

Odin 3 AMOLED. AYN's Android pixel shifter/refresher is **not** on Batocera.

## Patch 11 — what it does

- After **3 min** idle (configurable): dims panel to **20%** (sysfs only).
- **Does not** change `display.brightness` in Batocera settings.
- On button press or leaving Steam: restores **your ES brightness setting**.
- Adjustable in **Batocera Control → OLED** or `settings.conf`.

Config: `/userdata/system/configs/odin-oled-care/settings.conf`

## Without the patch

In ES: set screensaver (3–5 min), brightness ~70%, avoid static HUD at 100% for hours.

## Stuck at idle brightness?

```bash
batocera-brightness $(batocera-settings-get display.brightness)
bash /userdata/Batocera-Odin3-Patches/patches/11-oled-care/install.sh
```

Log: `/userdata/system/logs/odin-oled-care.log`
