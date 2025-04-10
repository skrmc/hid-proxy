# HIDEx: HID Gadget Proxy

**HIDEx** is a userspace application written in Rust that captures mouse events from Linux input devices (`/dev/input/event*`) and converts them as USB HID reports via the USB Gadget interface (`/dev/hidgX`). It enables devices such as RPi Zero or 4B to forward input events with minimal latency.

## Performance

Latency is measured by synchronizing timestamps between:

- The device emitting events (Raspberry Pi, using evdev)
- The host system receiving HID input (via USB)

| Metric             | Rust Implementation  | Go Implementation |
|--------------------|----------------------|-------------------|
| Average latency     | 956 µs               | 2122 µs           |
| Minimum latency     | 321 µs               | 752 µs            |
| Maximum latency     | 1459 µs              | 3116 µs           |
| Median latency      | 937 µs               | 2209 µs           |
| Standard deviation  | 352 µs               | 672 µs            |

HIDEx achieves sub-millisecond average latency with significantly reduced jitter.
