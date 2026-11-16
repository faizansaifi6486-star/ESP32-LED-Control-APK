# ESP32 LED Control (Android, Bluetooth Classic SPP)

## Build
1. Open this folder in Android Studio (Koala or newer) and let Gradle sync.
2. Run on a physical phone (emulators have no Bluetooth). minSdk 29 (Android 10), targetSdk 35.

## ESP32
Flash `esp32_sketch/ESP32_LED_CONTROL/ESP32_LED_CONTROL.ino` to a classic ESP32
(S3/C3/C6 do not support Bluetooth Classic). Change the pin numbers if needed.

## First use
1. Pair `ESP32_LED_CONTROL` in the phone's Bluetooth settings (the app's "Pair / Settings" button opens it).
2. Open the app, allow **Nearby devices** (Android 12+), select the device, tap **Connect**.

## Commands
| Char | Action | Char | Action |
|------|--------|------|--------|
| `1` | LED 1 ON | `5` | Buzzer ON |
| `2` | LED 1 OFF | `6` | Buzzer OFF |
| `3` | LED 2 ON | `A` | ALL ON |
| `4` | LED 2 OFF | `B` | ALL OFF |

The ESP32 should answer each command with one line (`println`), e.g. `LED 1 ON`.

## Permissions
- Android 10–11: `BLUETOOTH`, `BLUETOOTH_ADMIN` (install-time, `maxSdkVersion=30`).
- Android 12+: `BLUETOOTH_CONNECT` (runtime "Nearby devices"). No scan, no location needed, because the app only uses already-paired devices.
- No `INTERNET` permission: everything works offline.
