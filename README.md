# 🔋 Lovelace Battery Level Display for Home Assistant

- 📊 Template sensor mapping raw battery levels to: 0, 5, 15, 35, 50, 75, 90, 100
- 🧱 Lovelace card layout using `custom:button-card` and `custom:layout-card`
- 🖼️ Battery icons in `/config/www/battery/`
- 📱 Multi-device display (2 or 5 devices)

---

## 🔧 Installation

### 1. Upload Battery Icons

Put the following files in `/config/www/battery/`:

- `battery_0.png`
- `battery_5.png`
- `battery_15.png`
- `battery_35.png`
- `battery_50.png`
- `battery_75.png`
- `battery_90.png`
- `battery_100.png`

---

## 🖼️ Battery Icon Previews

| Level | Preview |
|-------|---------|
| 0%    | ![0%](./battery/battery_0.png) |
| 5%    | ![5%](./battery/battery_5.png) |
| 15%   | ![15%](./battery/battery_15.png) |
| 35%   | ![35%](./battery/battery_35.png) |
| 50%   | ![50%](./battery/battery_50.png) |
| 75%   | ![75%](./battery/battery_75.png) |
| 90%   | ![90%](./battery/battery_90.png) |
| 100%  | ![100%](./battery/battery_100.png) |

---

## 📷 Preview: 2 Devices

![Battery Preview (2 Devices)](./screenshot.png)

---

## 📷 Preview: 5 Devices

![Battery Preview (5 Devices)](./screenshot_3.png)

