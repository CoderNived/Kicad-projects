# ⚡ Power Chain Build Guide

This guide walks you through building a basic **AC → DC power chain** with a bridge rectifier, filter capacitor, voltage regulator, and load.  
Mentors will check your circuit with a multimeter (DMM) and oscilloscope (DSO).  

---

## 📝 Step A — Plan (5 minutes)

1. **Choose your regulator:**
   - `7805` → Fixed 5 V output (simple, common).
   - `LM317` → Adjustable output (needs resistors).
   - Switching module → More efficient (if allowed).

2. **Prepare heatsink:**  
   - For `7805`, attach a heatsink if current > 100 mA.

3. **Select test load:**
   - `33 Ω, 5 W` → ~150 mA load.
   - `16 Ω, 5 W` → ~300 mA load.
   - Add an **LED + 330 Ω resistor** in parallel as a power indicator.

---

## 🔌 Step B — Build Rectifier

1. **Using bridge rectifier IC (easy):**
   - Connect AC wires to the `~ ~` pins.
   - `+` = DC positive, `-` = DC negative/ground.

2. **Using 4 diodes (manual bridge):**
   - Arrange 4 diodes in a diamond.
   - AC input to two opposite corners.
   - Remaining corners = +DC and -DC.
   - Stripe side of diode (cathode) points to positive node.

---

## 🛢️ Step C — Add Bulk Filter

1. Connect a **large electrolytic capacitor** (10,000 µF, 25 V) across DC + and DC –.  
   - Long leg = positive.  
   - Short leg = negative (ground).  
   ⚠️ Check polarity carefully.

2. Add a **0.1 µF ceramic capacitor** in parallel (filters high-frequency noise).

3. Add a **100 kΩ, 1 W resistor** across the capacitor (bleeder) so it discharges safely after power-off.

---

## 🎚️ Step D — Voltage Regulator

1. Connect DC + to **regulator IN**, DC – to **GND**.  
2. Take regulated voltage from **OUT**.  
3. Add capacitors close to pins:
   - Input side: 0.33 µF (ceramic) + 10 µF (electrolytic).
   - Output side: 0.1 µF (ceramic) + 10 µF (electrolytic).
4. Attach heatsink if load >100 mA.

---

## 💡 Step E — Load & Indicators

1. Connect **33 Ω, 5 W resistor** across +5 V and GND (dummy load).  
   - Use **16 Ω, 5 W** for higher current (~300 mA).  

2. Connect **LED + 330 Ω resistor** in parallel as a visual "power ON" indicator.  

3. Verify:
   - **Multimeter (DMM):** Output should be ~5.0 V.  
   - **Oscilloscope (DSO):**
     - At capacitor: ripple (sawtooth at 100 Hz).  
     - At regulator output: flat line with <50 mV ripple.  

---

## ✅ Quick Recap Flow

