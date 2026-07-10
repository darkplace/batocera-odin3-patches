# Suspend / deep sleep freeze

**Symptom:** Console freezes after long idle sleep. Fix: Vol− + Power.

**Patch 10** forces `s2idle` and runs resume recovery (remount UFS, restart ES/Sway).

```bash
cat /sys/power/mem_sleep          # should show [s2idle]
tail -50 /userdata/system/logs/odin-resume-fix.log
```

If it still freezes:

```bash
batocera-settings-set system.suspendmode fake
```

`fake` turns off the panel without deep RAM suspend (safer, uses more battery in sleep).

Install: `bash patches/10-suspend-resume-fix/install.sh`
