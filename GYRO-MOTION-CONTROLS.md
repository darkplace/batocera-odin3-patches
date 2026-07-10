# Gyro / motion controls

**Built-in Odin 3 gyro is not exposed on this Batocera build.**

The `AYN Odin3 Gamepad` input has sticks and buttons only — no accelerometer/gyro axes. Yuzu and Cemu motion options have nothing to read.

## Workarounds

- External controller with gyro (Switch Pro, DualSense, Joy-Con)
- Phone DSU app (Cemu / Dolphin)
- Wait for AYN/Batocera to expose the IMU in a future kernel

Checked: `/sys/bus/iio/devices/` empty, no motion in `evdev` caps on `event2`.
