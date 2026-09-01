# MSI ARMOR GTX 960 4GB RnD & QA

| Parameter | Specification / Metadata |
| :--- | :--- |
| **Test Subject** | NVIDIA GeForce GTX 960 (4GB GM206 / Stock VBIOS 130W) |
| **Category** | Hardware Recovery, Firmware Flashing & Thermal Optimization |
| **Author / Engineer** | RinMP3 |
| **Equipment & TIM Used** | Thermal Grizzly Hydronaut Pro, 2x Arctic P12 PWM PST, NVIDIA DP Firmware Updater, NVFlash |
| **Date** | August 24, 2026 |

### Executive Summary & Key Validation Metrics

| Metric | Baseline / Initial State | Post-Rework / Modded State | Operational State |
| :--- | :---: | :---: | :---: |
| **Display Output** | Black Screen on 3x DP (UEFI) | Fully Operational (UEFI) | DP FW Updated |
| **Max Thermal Load (OCCT)** | `82.0 °C` (No TIM) | **`50.0 °C`** (Hydronaut Pro + 2x P12 Pro PST) | -32.0 °C Delta |
| **Hotspot Delta ($\Delta T$)** | Throttling / Unmeasurable | **`9.0 °C`** ($31.8\text{ °C}$ Die / $40.8\text{ °C}$ Hotspot) | Optimal TIM Contact |
| **Power Draw / Limit** | `130 W` (Stock VBIOS) | **`163 W`** (Custom VBIOS) | Unlocked |

 **Audit Objectives & Scope:** Diagnostic troubleshooting, GOP firmware recovery, changing thermal paste and pads, custom VBIOS flashing, and overclocking validation of a legacy GTX 960 platform.

### Test Rig & Methodology

* **CPU:** AMD Ryzen 7 5800X (Overclocked, PPT 124W)
* **GPU Under Test:** NVIDIA GeForce GTX 960 4GB (GM206)
* **TIM & Cooling:** Thermal Grizzly Hydronaut Pro, 1.0–1.5mm Thermal Pads, 2x Arctic P12 Pro PST (Ghetto Mod)
* **Software & Telemetry:** NVIDIA DisplayPort Firmware Updater, MSI Afterburner, OCCT v12+, Unigine Superposition

### Hardware Recovery & Firmware Restoration
* **PCIe Interface & Power Rail Diagnostics:** Physical probing verified 100% signal continuity and nominal voltage delivery across all PCIe slot edge contacts (+12V_BUS, +3.3V_BUS rails and input protection fuses/shunts).
* **Display Controller Isolation:** Card exhibited no display output across 3x DisplayPort under native motherboard UEFI mode, triggering bootloops with two GPUs installed.
* **CSM Workaround:** Enabling CSM and disabling Re-Bar restored display output, confirming a legacy Maxwell VBIOS GOP firmware bug.
* **Firmware Update:** Flashed the GPU using NVIDIA DisplayPort Firmware Updater, permanently restoring native UEFI boot and DP compatibility.

### Thermal Inspection & Cooling Rework

| Subsystem | Original Condition (As Received) | Rework / Modification | Operational Result |
| :--- | :--- | :--- | :---: |
| **Thermal Paste** | No TIM or Pads | Applied **Thermal Grizzly Hydronaut Pro** | Max `50.0 °C` under load |
| **Thermal Pads** | Missing (exposed VRM) | Replaced with $1.0\text{ mm} - 1.5\text{ mm}$ pads | Stable VRM thermals |
| **Fan Array** | Stock shroud removed | 2x **Arctic P12 Pro PST** (Ghetto Mod) | `30.0 °C` Idle / `50.0 °C` Peak |

 **Key Engineering Insight (Thermal & Silicon Performance):** The GPU arrived without thermal paste and missing thermal pads. Despite reaching `82.0 °C` during initial dry testing, direct-die application of Hydronaut Pro and high-static pressure 120mm fans dropped peak load thermals to `50.0 °C` with a tight `9.0 °C`  delta ($31.8\text{ °C}$ die vs $40.8\text{ °C}$ hotspot).

### Overclocking & Custom VBIOS Validation

* **VBIOS Power Limit:** Flashed custom VBIOS expanding power target headroom up to `163 W` real board draw (vs `120-130 W` stock).
* **Core Frequency:** Boosted to **`1532.00 MHz`** (`+204 MHz` offset in MSI Afterburner).
* **Memory Frequency:** Pushed to **`4130.00 MHz`** (`+619 MHz` offset).
* **Voltage Profile:** Core Voltage measured at `1.032 V` average (`1.200 V` maximum peak, `1.006 V` minimum).
* **Benchmark Result:** Achieved **`1322 points`** in Unigine Superposition, 25th place at the moment (1080P Xtreme profile).

### Final R&D / QA Engineer Verdict

The **NVIDIA GeForce GTX 960** platform was successfully recovered from a soft-bricked UEFI GOP state via DisplayPort firmware restoration. Following complete thermal rework with Thermal Grizzly Hydronaut Pro, custom dual-fan cooling, and VBIOS power limit expansion, the card achieved outstanding thermal efficiency ($50.0\text{ °C}$ max under extreme load) and stability at $1532\text{ MHz}$ core / $4130\text{ MHz}$ memory clock speeds.

<details>
  <summary><b> Photo Gallery</b></summary>
  <br>
<img width="4032" height="3024" alt="IMG_1837" src="https://github.com/user-attachments/assets/ab683c9b-5f43-4c98-94fd-b650856ca20f" />
<img width="3884" height="2913" alt="IMG_1836" src="https://github.com/user-attachments/assets/fe31c552-95bb-4771-89d6-36955a3c8a99" />
<img width="4032" height="3024" alt="IMG_1842" src="https://github.com/user-attachments/assets/2ef9a908-901b-44ec-b325-3ac58c06972b" />
<img width="4032" height="3024" alt="IMG_1844" src="https://github.com/user-attachments/assets/d1aded60-be8d-4071-9934-6a7056a1aa8b" />
<img width="4032" height="3024" alt="IMG_1845" src="https://github.com/user-attachments/assets/feafea7f-8882-439a-b543-6c5e3d8c1947" />
<img width="4032" height="3024" alt="IMG_1847" src="https://github.com/user-attachments/assets/541b9ba1-0a49-494a-9f02-f9480e6be0a5" />
<img width="4032" height="3024" alt="IMG_1848" src="https://github.com/user-attachments/assets/0dfb4192-6173-4a45-9666-9fe414d6e242" />
<img width="5712" height="4284" alt="IMG_1874" src="https://github.com/user-attachments/assets/40c3c8db-c10a-43b1-abae-c48543328138" />
<img width="4032" height="3024" alt="IMG_1890" src="https://github.com/user-attachments/assets/3dc40dd6-ecc4-4b26-870f-ecf6023a2f0c" />
<img width="1073" height="215" alt="photo_2026-08-24_20-38-13" src="https://github.com/user-attachments/assets/85da945c-3c8a-4168-918c-2f1fe959bf1b" />
<img width="4032" height="3024" alt="IMG_1891" src="https://github.com/user-attachments/assets/37f720c1-9065-41bf-a710-0bea1c68a6b2" />
<img width="4032" height="3024" alt="IMG_1892" src="https://github.com/user-attachments/assets/693aef92-3dba-43d4-8130-01eea2ca11d5" />

</details>
