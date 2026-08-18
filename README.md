# 808nm IR Laser Diode Array System for 12-Well Cell Culture Plates

A complete hardware setup and 4-piece 3D-printed enclosure system designed to align an array of **808nm Near-Infrared (NIR) laser diodes** over standard 12-well cell culture plates, powered by an LM2596 Constant-Current (CC) driver circuit.

---

## ⚠️ Optical Safety Warning

* **Wavelength:** 808nm (Near-Infrared / Invisible to the naked human eye).
* **Mandatory PPE:** Laser safety glasses with certified optical density for **808nm (OD4+ or higher / EN 207 / ANSI Z136)**.
* **Caution:** Standard clear workshop safety goggles (e.g., ANSI Z87.1 / Z87+S) **do not provide protection** against direct or scattered infrared laser beams.

---

## 🔬 Experimental Compatibility (12-Well Plate)

The top mounting fixture is engineered around the standard footprint of a **12-well cell culture plate ($3 \times 4$ matrix)**:

* **Grid Capacity:** Designed to hold up to 12 emitters.
* **Current Configuration:** Populated with **10 active 808nm laser diodes** wired in series.
* **Expandability:** The remaining 2 positions are left unpopulated and can accommodate additional diodes in future revisions.

![12-Well Cell Culture Plate Alignment](docs/images/12_well_plate_layout.png)

---

## 🖨️ 3D Enclosure Structure

The enclosure consists of a modular 4-piece assembly:

1. **Base Box (`01_base_box.stl`):** Main structural body providing elevation and housing for the lower stages.
2. **Internal Drawer (`02_internal_drawer.stl`):** Sliding tray designed for easy insertion, positioning, and removal of the 12-well cell culture plate.
3. **Laser Mounting Plate (`03_laser_mount.stl`):** Alignment matrix positioned directly above the plate, securing the 5.6mm (TO-18) laser diode packages.
4. **Top Cover (`04_top_cover.stl`):** Upper protective lid enclosing the diode wiring and preventing external interference.

![3D Printed Enclosure Assembly](docs/images/enclosure_exploded_view.png)

---

## ⚡ Electrical Specifications & Power Circuit

The 10 laser diodes are wired strictly in **series**, ensuring that every emitter receives identical driving current.

| Parameter | Specification |
| :--- | :--- |
| **Laser Diodes** | 10x 808nm Infrared Laser Diodes (5.6mm / TO-18) |
| **Forward Voltage ($V_f$) per Diode** | ~1.8V to 2.2V |
| **Total Forward Voltage ($V_{total}$)** | ~18.0V to 22.0V |
| **Operating Current ($I_f$)** | **250mA** (0.25A Constant Current) |
| **Current Regulation** | LM2596 Step-Down Module (with CC/CV trimpots) |
| **Power Supply Input** | **24V DC** or **32V DC** (1A minimum) |

> 📌 **Power Supply Note:** Due to the internal dropout voltage of the LM2596 (~1.5V–2.0V), a 24V DC source operates near the upper voltage threshold required for 10 diodes in series (~22V). If the circuit fails to reach 250mA under full load, use a **32V DC** power supply to provide adequate operating headroom.

![Circuit Wiring Diagram](docs/images/circuit_schematic.png)

---

## 📌 Diode Pinout Reference (TO-18 / 5.6mm - Style C)

Viewed from the **bottom** (pins facing you, metal case notch positioned at the top):

```text
               CASE NOTCH
                 (Top)
                   │
               ┌───┴───┐
            ──┤    ①    ├──
           /   \ (Anode) /   \
          │     \  (+)  /     │
          │      \     /      │
          │   ②   \___/   ③   │
          │(Cathode)    (PD)  │
          │  (-)              │
           \                 /
            ──┤             ├──
               └───────────┘
