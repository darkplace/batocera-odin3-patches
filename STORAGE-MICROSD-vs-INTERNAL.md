# Storage: microSD vs UFS

Odin 3 typical layout:

| Where | What |
|-------|------|
| **microSD** (`/userdata`, exFAT) | ROMs, saves, configs, themes, services |
| **UFS** (`/dev/sda19`, ext4 → `/userdata/ufs`) | Steam, Wine, Decky, PC games |

Check: `lsblk -f` and `mount | grep -E 'userdata|ufs|bind'`

---

## Scenario A — SD + UFS (recommended)

Emulators on SD, Steam/Wine/Decky on internal ext4.

**Run:** `./apply-all.sh`

Patch 01 binds:

- `/userdata/ufs/games` → `/userdata/roms/windows`
- Wine bottles, Steam, `.steam`, Decky homebrew

---

## Scenario B — SD only

No internal UFS used for Steam/Wine.

**Run:** `./apply-sd-only.sh` (skips patch **01**, uses `install-sd.sh` for Decky/Control)

Steam/Wine on exFAT alone is **not recommended** (symlinks, permissions).

---

## If UFS partition differs

Edit `/dev/sda19` in `patches/01-ufs-bind-mounts/custom_service` if `lsblk` shows another device.
