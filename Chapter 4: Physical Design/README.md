
## 📘 Chapter 4: Physical Design
- 4.1 Floorplanning and die area  
- 4.2 Standard cell placement  
- 4.3 Clock Tree Synthesis (CTS)  
- 4.4 Routing (global and detailed)  
- 4.5 Power distribution (VDD/VSS)  
- 4.6 Congestion and utilization

---

# Chapter 4: Physical Design

## 4.1 Floorplanning and Die Area

Floorplanning is the first step in physical design where the **chip layout structure is defined**. It determines the size of the chip (die area), placement of core region, I/O pins, and power distribution.

## 📌 Concept

- **Die Area** → Total chip size  
- **Core Area** → Region where standard cells are placed
```Die Area = Core Area + IO + Margins```

## ⚙️ Basic Layout Structure

```
+---------------------------+
| Die Area                  |
| +---------------------+   |
| | Core Area |             |
| | (Standard Cells) |      |
| +---------------------+   |
| IO Pins / Pads            |
+---------------------------+
```

<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/cf1588f8-20d5-4f19-8e15-74ccbff2a32c" />

## 🔧 Floorplanning Goals

- Define chip dimensions  
- Allocate space for logic cells  
- Plan power distribution (VDD/GND)  
- Place IO pins properly  

## 📊 Important Parameters

### 1. Die Area
- Total chip boundary  

### 2. Core Area
- Area used for logic placement  

### 3. Utilization
```Utilization = (Cell Area / Core Area) × 100```

- Typical value: 50%–70%  

### 4. Aspect Ratio
```Aspect Ratio = Height / Width```

- Usually close to 1 (square shape preferred)

## Importance

- Affects placement and routing efficiency  
- Impacts power, performance, and area  
- Poor floorplan → congestion and timing issues  

## Key Points

- Defines chip structure before placement  
- Controls area and layout efficiency  
- Critical for successful physical design flow  

---

</br>

#  4.2 Standard Cell Placement

Standard cell placement is the process of arranging synthesized logic cells (standard cells) within the core area of the chip. It is performed after floorplanning and before routing.

## 📌 Concept

- Logic from synthesis is converted into **standard cells**  
- Placement decides **where each cell is located** on the chip  
```Netlist → Standard Cells → Placement in Core Area```

## Placement Flow

### 1. Global Placement
- Rough placement of cells  
- Optimizes for wirelength and congestion  

### 2. Detailed Placement
- Fine adjustment of cell positions  
- Ensures no overlaps and proper alignment  

## Placement Structure
```
| Row 1: [Cell][Cell][Cell] |
| Row 2: [Cell][Cell][Cell] |
| Row 3: [Cell][Cell][Cell] |
```

- Cells are placed in **horizontal rows**  
- Rows are aligned with **power rails (VDD/GND)**  

## Key Objectives

- Minimize wirelength  
- Reduce congestion  
- Improve timing performance  
- Avoid cell overlap  


## Important Terms

### 1. Standard Cell
- Pre-designed logic block (AND, OR, INV)

### 2. Placement Rows
- Fixed horizontal regions for cell placement  

### 3. Congestion
- Overcrowding of cells and routing paths  

### 4. Density

```Density = Cell Area / Available Area```


## Challenges

- High density → routing difficulty  
- Poor placement → timing violations  
- Uneven distribution → congestion  

## Key Points

- Converts netlist into physical layout positions  
- Done before routing  
- Directly impacts timing, power, and area  

---

# 4.3 Clock Tree Synthesis (CTS)

Clock Tree Synthesis (CTS) is the process of distributing the clock signal from the clock source to all sequential elements (flip-flops) in the design while minimizing delay, skew, and power.


##  Concept

- Clock signal must reach all flip-flops  
- Delay should be balanced across the design  

```Clock Source → Buffers/Inverters → Flip-Flops```

##  Clock Tree Structure
```
    Clock Source
         |
    ------------
    |          |
 Buffer      Buffer
  |            |
  FF1 FF2 FF3 FF4
```
- Tree-like structure distributes clock  
- Buffers are inserted to control delay  

## Key Objectives

- Minimize **clock skew**  
- Reduce **clock latency**  
- Ensure balanced clock distribution  
- Improve timing reliability  

## Important Terms

### 1. Clock Skew
- Difference in clock arrival time at flip-flops  

### 2. Clock Latency
- Delay from clock source to flip-flop  

### 3. Clock Jitter
- Variation in clock signal timing  

### 4. Buffer Insertion
- Used to drive clock signal across large distances 

---

#  4.4 Routing (Global and Detailed)

Routing is the process of connecting placed standard cells using metal wires to form the complete circuit. It is performed after placement and is divided into global routing and detailed routing.

##  Concept

- Connect all cells based on netlist  
- Use metal layers (Metal1, Metal2, etc.)  
- Ensure no design rule violations  

```Placed Cells → Routing → Connected Circuit```


##  Types of Routing

### 1. Global Routing
- Plans approximate paths for connections  
- Divides chip into routing regions  
- Estimates congestion and wirelength  


### 2. Detailed Routing
- Finalizes exact wire paths  
- Assigns specific metal layers and tracks  
- Ensures no overlaps or violations  
* Precise wire connection

## 📊 Routing Layers

- Metal1 → Local connections  
- Metal2/Metal3 → Long-distance routing  
- Vias → Connect different metal layers  

```
Metal1 ↑
|
Via
|
Metal2 →
```

##  Key Objectives

- Connect all nets correctly  
- Minimize wirelength  
- Avoid congestion  
- Meet timing constraints  

---

## Important Terms

### 1. Net
- Connection between cells  

### 2. Via
- Vertical connection between metal layers  

### 3. Track
- Predefined routing path  

---

# 4.5 Power Distribution (VDD / VSS)

Power distribution is the process of delivering stable power supply (VDD) and ground (VSS) to all cells in the chip through a structured network called the Power Distribution Network (PDN).


##  Concept

- VDD → Supply voltage  
- VSS (GND) → Ground reference  

All standard cells require both VDD and VSS to operate correctly.

```Power Source → Power Grid → Standard Cells```


##  PDN Structure
```
VDD ======================
|| || || ||
|| || || ||
VSS ======================
```

- Horizontal and vertical metal lines form a **grid**
- Power is distributed uniformly across the chip  


##  Key Components

### 1. Power Rails
- Run along standard cell rows  
- Provide local power connection  

### 2. Power Straps
- Wider metal lines for high current flow  

### 3. Power Rings
- Surround the core area  
- Provide stable supply from IO pads
  
### 4. Vias
- Connect power between different metal layers
  

## Important Parameters

### 1. IR Drop
- Voltage drop due to resistance  ```V = I × R```
- High IR drop → incorrect circuit operation  

### 2. Current Density
- Amount of current per unit area  
- High value → reliability issues  

### 3. Electromigration
- Movement of metal atoms due to high current  
- Can damage wires over time  

---

#  4.6 Congestion and Utilization

Congestion and utilization are key metrics in physical design that affect placement, routing, and overall chip performance.

## Utilization

Utilization defines how much of the available core area is occupied by standard cells.

```Utilization = (Cell Area / Core Area) × 100```

### Example
```
Cell Area = 500 µm²
Core Area = 1000 µm²

Utilization = 50%
```

###  Interpretation
- Low utilization (<50%) → wasted area  
- Optimal (50–70%) → balanced design  
- High (>80%) → routing difficulty  

##  Congestion

Congestion occurs when too many cells or wires are crowded in a specific region, making routing difficult.

```More cells + more connections → higher congestion```


## Congestion Representation
```
Low Congestion: High Congestion:

[Cell] [Cell] [Cell][Cell][Cell]
| | ||||||||||||||||
[Cell] [Cell] [Cell][Cell][Cell]
```

## Causes of Congestion

- High cell density  
- Poor placement  
- Complex interconnections  
- Limited routing resources  

## Effects of Congestion

- Routing failures  
- Increased wire delay  
- Timing violations  
- DRC errors 






















