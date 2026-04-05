# 🦁 Animal Kaiser – PC Playable Setup
<img width="540" height="360" alt="image" src="https://github.com/user-attachments/assets/40efcb0b-98b6-4d27-babf-284153f92e8e" />

A fan-preservation project for playing **Animal Kaiser** (Ver 1–6) and **Animal Kaiser Evolution** (Evo 1–8) on PC using the [Play! PS2/Arcade Emulator](https://github.com/jpd002/Play-) and the [AK Card Scanner](https://github.com/Gama-Tech/AK-Card-Scanner-Releases).

> **Note:** This project is for archival and preservation purposes only. It does not distribute copyrighted ROM files.

---

## 📁 Repository Structure

```
Animal Kaiser Playable/
│   Animal Kaiser Auto Clicker.py    # Auto-clicker utility script
│   List of Barcodes.xlsx            # Barcode reference list for card scanning
│
├───Archive of Cards/                # Scanned card lists and leaflets by version
│   ├───Ver 1 – Ver 6/               # Original Animal Kaiser versions
│   └───Evo 1 – Evo 8/              # Evolution series
│
├───Card Scanner/                    # AK Card Scanner binaries (see below)
│   ├───AKCardScanner.exe
│   └───...
│
├───Play Emulator/                   # Play! emulator binaries (see below)
│   ├───Play-x86-32.exe
│   └───Play-x86-64.exe
│
└───ROMS/                            # Place your ROM files here (not included)
    ├───akaiser/
    │       akaiser.zip
    │       kp005a_ana1004-na-b.ic26
    └───akaievo/
            akaievo.zip
            kp012b_k9k8g08u0b.ic31
```

---

## ⚙️ Prerequisites

- **OS:** Windows only (macOS has known compatibility issues — see [Known Issues](#-known-issues))
- **[Play! Emulator](https://github.com/jpd002/Play-)** — PS2/Arcade emulator used to run Animal Kaiser
- **[AK Card Scanner](https://github.com/Gama-Tech/AK-Card-Scanner-Releases)** — Sends card barcodes to the emulator via HTTP

---

## 🛠️ Setup Instructions

### Step 1 – Install Play! Emulator

1. Navigate to the `Play Emulator/` folder.
2. Run the appropriate version for your system:
   - **`Play-x86-64.exe`** — for 64-bit Windows (recommended)
   - **`Play-x86-32.exe`** — for 32-bit Windows
3. Run the emulator **at least once** and then close it. This creates the `Play Data Files` folder in your Documents directory.

---

### Step 2 – Set Up ROM Folders

1. Open `Documents\Play Data Files\` and navigate to the `arcaderoms` folder.
2. Create two subfolders inside `arcaderoms`:
   - `akaiser`
   - `akaievo`
3. Copy the ROM files from the `ROMS/` folder into the corresponding folders:
   - Copy `kp005a_ana1004-na-b.ic26` → `arcaderoms/kaiser/`
   - Copy `kp012b_k9k8g08u0b.ic31` → `arcaderoms/kaievo/`
   - The `.zip` files (`akaiser.zip`, `akaievo.zip`) should also be copied to the respective     `arcaderoms/` subfolders alongside the `.ic26`/`.ic31` files.

---

### Step 3 – Configure Play! Emulator

1. Open **Play!** and go to **Options > Settings > General**.
2. Enable **Arcade I/O HTTP Server**.


---

### Step 4 – Set Up AK Card Scanner

1. Locate the `Card Scanner/` folder.
2. Copy the entire folder to a convenient location (e.g. `Documents\Card Scanner\`).


> The [AK Card Scanner](https://github.com/Gama-Tech/AK-Card-Scanner-Releases) communicates with Play! via the Arcade I/O HTTP Server to simulate card scans.

---

### Step 5 – First Launch & Staff Menu Setup

1. Open **Play!** and load a supported version of Animal Kaiser (see [Known Issues](#-known-issues) for supported versions).
2. A **Card Reader Error** will appear on launch — this is expected.
3. **Press and hold `1`** to enter the Staff Menu.
4. Use the following controls to navigate:
   | Key | Action |
   |-----|--------|
   | `↑` / `↓` | Navigate menu |
   | `Z` | Confirm selection |
   | `1` (hold) | Stay in Staff Menu |

5. Make the following changes:
   - **Coin Options** → Enable **Free Play**
   - **Game Options** → Disable **Card Dispenser Enabled**
6. Press `Z` to confirm each setting **before** releasing `1`.
7. Release `1` to exit. The first load may take a while — if nothing happens, press and hold `1` again before releasing.

---

### Step 6 – Playing the Game

- **Left / Right buttons** in-game → `←` / `→` arrow keys
- When you reach the **card scanning screen**, switch to `AKCardScanner.exe` and input the barcode.
- Barcodes can be found in `List of Barcodes.xlsx` and in the `Archive of Cards/` folder.

> ⚠️ **Important:** The game pauses when Play! loses window focus. After sending a barcode via the Card Scanner, **click back into Play!** to resume.

---

## ⚡ Performance Optimisation (Fix Lag)

If the game runs slowly, apply the following fixes:

**In Play! — Options > Settings > General:**
- Disable **Cap Frame Rate to Video Refresh Rate**

**In Play! — Options > Settings > Video:**
- Tick **all checkboxes**
- Set **Presentation Mode** to `Original Size`

**In Play! — Options > Settings > Audio:**
- Disable **Audio**

**In Windows Task Manager:**
1. Open Task Manager (`Ctrl+Shift+Esc`)
2. Go to **Processes**, right-click `Play.exe` → **Go to details**
3. In **Details**, right-click `Play.exe` → **Set Priority** → **High**

> ⚠️ You must **repeat the priority step every time** you open Play!, even after a restart.

---

## 🐛 Known Issues

| Issue | Details |
|-------|---------|
| **Limited version support** | Only **King of Animals Ver 1 & 2** and **Evolution Evo 1–8** are playable. Ver 3–6 and Great Animal Kaiser are not available. |
| **Card archive gaps** | The `Archive of Cards/` folder does not include Great Animal Kaiser or promo/tournament cards. |
| **Incomplete barcode list** | Not all barcodes are known or verified in `List of Barcodes.xlsx`. |
| **Card Reader error on relaunch** | Even after initial setup, reopening the same version may show the Card Reader error again. Hold `1` to enter the Staff Menu and release — do not change any settings this time. |
| **Vertical lines on screen** | Caused by some GPU configurations (particularly AMD Radeon/Ryzen). Go to **Options > Settings > Video** and adjust **Vulkan settings** if available. If pressing **Show Vulkan Device Info...** shows incompatibility, no fix is available. |
| **macOS** | Play! is only reliably supported on Windows. macOS users will encounter significant issues. |

---

## 🔮 Future Work / Ideas

- **Emulator updates:** [Play!](https://github.com/jpd002/Play-) has not seen active updates in at least 2 years at the time of writing, which limits version support. Contributions to the emulator upstream would benefit this project.
- **Complete NAND archive:** Finding complete NAND dumps for all versions — especially Great Animal Kaiser — would enable broader preservation, but is extremely challenging.
- **Great Animal Kaiser support:** Great Animal Kaiser introduces additional mechanics and new card types, making emulation significantly more complex.
- **Cross-platform support:** Investigating alternative emulators or WINE configurations that could bring macOS/Linux support.

---

## 🙏 Credits & References

- **[Play! Emulator](https://github.com/jpd002/Play-)** by jpd002 — PS2/Arcade emulator powering this setup
- **[AK Card Scanner](https://github.com/Gama-Tech/AK-Card-Scanner-Releases)** by Gama-Tech — Card barcode scanner integration for Play!

---

## ⚠️ Disclaimer

This repository is for **preservation and archival purposes only**.
