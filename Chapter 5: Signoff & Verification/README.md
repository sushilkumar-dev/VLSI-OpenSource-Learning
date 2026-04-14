# 📘 Chapter 5: Signoff & Verification

Signoff is the final stage of ASIC design where the layout is verified for correctness, manufacturability, and performance before fabrication.

---

## 5.1 Design Rule Check (DRC)

DRC verifies whether the layout follows manufacturing rules defined by the technology (Sky130).

### Checks Include
- Minimum width  
- Minimum spacing  
- Overlap rules  

### Importance
- Ensures layout can be fabricated without defects  

---

## 5.2 Layout vs Schematic (LVS)

LVS checks whether the **layout matches the original circuit schematic**.

###  Concept
```Schematic (Netlist) == Layout (Extracted Netlist)```


###  Importance
- Ensures no missing or incorrect connections  

---

## 5.3 Parasitic Extraction (RC)

Extraction calculates parasitic **resistance (R)** and **capacitance (C)** from layout.

### Concept
- Wires introduce delay due to RC effects  
```Delay ≈ R × C```


###  Importance
- Used for accurate timing analysis  

---

##  5.4 Power Analysis (Dynamic & Leakage)

Power consumption is analyzed after routing.

###  Types

- **Dynamic Power**
```P = α × C × V² × f```

- **Leakage Power**
- Power consumed even when circuit is idle  

###  Importance
- Critical for low-power design  

---

##  5.5 IR Drop Analysis

IR drop is the voltage drop in power network due to resistance.

###  Concept
```V = I × R```

- High current → voltage drop → incorrect operation  

###  Importance
- Ensures stable power delivery  

---

##  5.6 GDSII Generation (Final Chip Layout)

GDSII is the final output file sent for fabrication.

###  Contains
- All layers (metal, diffusion, poly)  
- Complete chip layout  

### Importance
- Directly used by semiconductor foundry to manufacture chip  

---

## Key Takeaways

- DRC → checks layout rules  
- LVS → verifies circuit correctness  
- RC extraction → accurate timing  
- Power analysis → efficiency  
- IR drop → power integrity  
- GDSII → final fabrication file  













