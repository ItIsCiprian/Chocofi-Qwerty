# 💡 Chocofi QWERTY — ZMK Firmware

Custom **ZMK** configuration for my split **Chocofi / Corne-style keyboard**, powered by **Nice!Nano v2** controllers and designed for efficiency, portability, and Bluetooth connectivity.

---

## ⚙️ Features

- Based on **Corne (crkbd)** layout — 3×6 + 3 per half (42 keys)
- Fully wireless via **ZMK + Nice!Nano v2**
- Three fully-defined layers:
  - 🏠 **Home (Base)** — QWERTY typing, modifiers on thumbs
  - 🔢 **Num/Symbols** — numbers, navigation, symbols
  - 🎧 **Nav/Media** — function keys, media, and Bluetooth control
- Custom **tap-hold behaviors** for:
  - Home-row mods (`hm`, `weak`, `shifthr`)
  - Dual-function keys on thumbs (`Ctrl/TAB`, `Opt/ESC`, etc.)
- Tap-dance behavior for **Backspace → Ctrl+Backspace**
- Combos for quick access (Escape, Dash, Caps Word, etc.)
- Macros for **Save (ESC : w ENTER)** and **Email insertion**
- Compatible with the **Keymap Editor** → [nickcoutsos.github.io/keymap-editor](https://nickcoutsos.github.io/keymap-editor/)

---

## ⌨️ Layers Overview

### 🏠 **Layer 0 — Base (QWERTY)**
TAB | Q | W | E | R | T | Y | U | I | O | P | BKSP
CTRL | A | S | D | F | G | H | J | K | L | ' | ;
SHFT | Z | X | C | V | B | N | M | , | . | / | ESC
⌥/ESC ⌘ ⌃/TAB ENTER L1/SPC L2/BSP

markdown
Copy code

### 🔢 **Layer 1 — Numbers / Symbols**
1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0
` |Home|PgUp|PgDn|End |← |↓ |↑ |→ | ;:
SHFT| | | | |- | = | [ | ] | |

markdown
Copy code

### 🎧 **Layer 2 — Functions / Media**
F1 |F2 |F3 |F4 |F5 |F6 |F7 |F8 |F9 |F10
F11|F12|Prev|Play|Next |Mute|Vol-|Vol+|Br-|Br+
BT0 | BT1 | BT2 | BT3 | BT4 |Clr |ClrAll|Next|Prev

yaml
Copy code

---

## 🛠️ Build Instructions

### Local Build
Make sure the Zephyr SDK and West are installed, then:
```bash
# Left half
west build -p -b nice_nano_v2 -- -DSHIELD="corne_left nice_view_adapter nice_view"

# Right half
west build -p -b nice_nano_v2 -- -DSHIELD="corne_right nice_view_adapter nice_view"
GitHub Actions Build
Your .github/workflows/build.yml already includes:

yaml
Copy code
include:
  - board: nice_nano_v2
    shield: corne_left nice_view_adapter nice_view
  - board: nice_nano_v2
    shield: corne_right nice_view_adapter nice_view
  - board: nice_nano_v2
    shield: settings_reset
Each push to main automatically builds left / right firmware and publishes artifacts under Releases.

📂 Repository Structure
bash
Copy code
config/
 ├── corne.keymap       # Full keymap definition (this file)
 ├── chocofi.conf       # Firmware + Bluetooth config
 ├── build.yaml         # Board/shield matrix for CI
 └── west.yml           # Module definitions
zmk/
 └── app/…              # ZMK source + Zephyr build system
🧠 Credits
ZMK Firmware

Corne Keyboard

Nick Coutsos Keymap Editor

Inspired by the Peter X. Jang 36-key layout

🪄 Author
ItIsCiprian Anescu
Test Engineer • Dev • Tinkerer
github.com/ItIsCiprian

“Refined simplicity meets firmware.”
— Built with love, layers, and logic.
