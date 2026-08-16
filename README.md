<div align="center">

# 📦 Universal OTA Incremental Applier

**Apply incremental (delta) OTA updates on top of a full OTA to reconstruct the final full system images.**

Works on any Android device using standard A/B `payload.bin` OTA updates — no AOSP build environment required.

</div>

---

## ✨ Features

| | |
|---|---|
| 🌍 **Universal** | Works on any A/B device shipping stock `payload.bin` OTAs — not limited to one brand |
| 📤 **Auto Extraction** | Automatically pulls `payload.bin` out of each OTA zip — no manual unzipping needed |
| 🚫 **No AOSP Build** | Unlike tools that depend on building `delta_generator` from full AOSP source |
| 🔗 **Chained Increments** | Apply as many incremental updates as you need, one after another |
| ⚡ **Simple CLI** | One command, no complicated setup |

---

## 📱 Device Support

This tool works with any Android device that ships OTA updates in the standard AOSP `payload.bin` format (Google's `update_engine` A/B update system). Support depends on the **OTA file format**, not the device brand.

**Known to use this format:**

Google (Pixel) • OnePlus • Oppo • Realme • Xiaomi / Redmi / POCO • Nothing • Motorola • ASUS (ROG Phone / Zenfone) • Nokia (HMD) • Lenovo • Sony (Xperia) • Fairphone • most other AOSP-based / GKI devices with A/B (seamless) updates

> 💡 **Not listed above?** If your device ships A/B updates as a `payload.bin` inside the OTA zip, it will most likely still work.

**❌ Not supported:** Samsung — Samsung OTAs use a proprietary container and delta format instead of `payload.bin`, so this tool cannot process them.

---

## 🛠️ Requirements

- 🐧 Linux or WSL environment — no WSL yet? 👉 [WSL + Ubuntu 22.04 setup guide](https://htmlpreview.github.io/?https://github.com/TropsPk/Universal-OTA-Incremental-Applier/blob/main/assets/wsl-ubuntu-2204-setup.html)
- `bash`
- `unzip`
- The full OTA package and any incremental OTA package(s), placed in the `packages` folder

---

## 🚀 Usage

**1.** Put your OTA packages in the `packages` folder.

**2.** Run:

```bash
./dump.sh FullPackage (optional)incremental1 (optional)incremental2
```

- **`FullPackage`** — name of the full update package, including the file extension (e.g., `ota.zip`)
- **`incremental1`** *(optional)* — name of the first incremental update package (e.g., `ota-1.zip`)
- **`incremental2`** *(optional)* — name of the second incremental update package (e.g., `ota-2.zip`)

**Example:**

```bash
./dump.sh ota_full.zip ota_incremental_1.zip ota_incremental_2.zip
```

Only have the full OTA, no incrementals?

```bash
./dump.sh ota_full.zip
```

---

## 📂 Output

Once finished, the extracted and merged raw partition images are saved to the **output** folder — ready for flashing, analysis, firmware extraction, or anything else you need.

---

## 📝 Notes

- ⚠️ Apply incremental packages **in the correct order** — each one must match the version that came before it in the chain.
- 📦 Large output files may be split into smaller parts automatically.

---

## 🙌 Credits

Built on [**luk1337**](https://github.com/luk1337)'s work.

