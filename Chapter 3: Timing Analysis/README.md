## 📘 Chapter 3: Timing Analysis
- 3.1 Setup time and hold time  
- 3.2 Slack and timing violations  
- 3.3 Critical path analysis  
- 3.4 Clock constraints and definitions  
- 3.5 Static Timing Analysis (STA)  
- 3.6 Multi-corner timing (tt, ss, ff)  




# Chapter 3: Timing Analysis

## 3.1 Setup Time and Hold Time

Setup time and hold time are fundamental timing constraints in synchronous digital circuits that ensure correct data transfer between flip-flops.

**Setup time** is the minimum time before the clock edge during which the input data must remain stable. If the data changes too close to the clock edge, the flip-flop may not capture the correct value, resulting in a setup violation.

**Hold time** is the minimum time after the clock edge during which the input data must remain stable. If the data changes too soon after the clock edge, the flip-flop may capture incorrect data, causing a hold violation.

In simple terms:
- Setup time → data must be stable **before** clock edge  
- Hold time → data must be stable **after** clock edge  

These constraints are critical for reliable circuit operation and are checked during Static Timing Analysis (STA) to avoid timing violations.

* Setup time </br>
<img width="975" height="492" alt="Screenshot from 2026-04-14 09-24-03" src="https://github.com/user-attachments/assets/54c08fe3-9b42-433b-ad64-feb554ce273c" /> </br>

* Hold time </br>
<img width="975" height="492" alt="Screenshot from 2026-04-14 09-24-15" src="https://github.com/user-attachments/assets/bed1b32a-33ee-4acc-9bb3-3925646779e1" /> </br>

---

# 3.2 Slack and Timing Violations

Slack is the difference between the required arrival time and the actual arrival time of a signal in a digital circuit. It indicates whether the design meets timing requirements or not.

**Slack = Required Time − Arrival Time**

- If Slack > 0 → Timing is met (safe)  
- If Slack = 0 → Just meets timing  
- If Slack < 0 → Timing violation  

## Example
- Required Time = 10 ns </br>
Arrival Time = 8 ns </br>
Slack = 10 - 8 = +2 ns → **No violation** </br>

- Required Time = 10 ns </br>
Arrival Time = 12 ns </br>
Slack = 10 - 12 = -2 ns → **Setup violation** </br>


## Types of Timing Violations

### 1. Setup Violation
- Occurs when data arrives **late**
- Slack becomes **negative**


### 2. Hold Violation
- Occurs when data changes **too early**
- Violates hold time requirement

---

#  3.3 Critical Path Analysis

Critical path is the **longest delay path** between two sequential elements (flip-flops) in a digital circuit. It determines the **maximum speed (clock frequency)** at which the circuit can operate.

## Concept

- Every path has some delay  
- The path with **maximum delay = Critical Path**  
- It limits the clock period  

Clock Period ≥ Critical Path Delay


## Example

Path 1 delay = 5 ns </br>
Path 2 delay = 8 ns </br>
Path 3 delay = 12 ns ← Critical Path </br>

So, </br>

Minimum Clock Period = 12 ns
Maximum Frequency ≈ 1 / 12 ns ≈ 83 MHz


## Path Representation

FF1 → Logic Gates → FF2 </br>

FF1    ──►    AND    ──►    OR    ──►    XOR    ──►    FF2 </br>
↑ total delay ↑ </br>

---

# 3.4 Clock Constraints and Definitions

Clock constraints define how the clock behaves in a digital design and are essential for accurate timing analysis. They inform synthesis and timing tools about clock frequency, period, and timing requirements.

## Clock Definition

A clock is a periodic signal that controls when data is captured in flip-flops.

Clock Period (T) = Time between two rising edges  
Frequency (f) = 1 / T  

## Clock Waveform

Clock: ────↑──────↑──────↑──── </br>
        |<-- T -->| </br>


##  Clock Constraint (SDC Example)

```tcl
create_clock -name clk -period 10 [get_ports clk]
```
* Period = 10 ns
* Frequency = 100 MHz

### Important Clock Parameters </br>
1. Clock Period </br> 
* Total time for one clock cycle </br>
* Determines circuit speed </br>

2. Clock Frequency </br>

```Frequency = 1 / Period```

3. Clock Latency
* Delay from clock source to flip-flop
4. Clock Uncertainty
* Variation due to jitter and noise
5. Clock Skew
* Difference in clock arrival time across flip-flops
  
---

# 3.5 Static Timing Analysis (STA)

Static Timing Analysis (STA) is a method used to verify the timing performance of a digital circuit **without applying input test vectors**. It checks whether all timing constraints (setup, hold, clock) are satisfied across all possible paths in the design.

## Concept

STA analyzes signal propagation delays through the circuit and ensures that data arrives within the required time limits.

```Slack = Required Time − Arrival Time```

If slack is negative → timing violation.

## Basic Flow

1. Read design (gate-level netlist)  
2. Apply timing constraints (clock, input/output delays)  
3. Calculate delays for all paths  
4. Check setup and hold timing  
5. Report violations  

## Types of Analysis

### 1. Setup Analysis
- Checks if data arrives **before clock edge**
- Detects setup violations  

### 2. Hold Analysis
- Checks if data remains stable **after clock edge**
- Detects hold violations
  
## Path Analysis

```FF1 → Combinational Logic → FF2```

STA checks delay of this path and verifies:

- Setup condition  
- Hold condition  

## Violations

- **Setup Violation** → Data arrives late  
- **Hold Violation** → Data changes too early  

---

# 3.6 Multi-Corner Timing (TT, SS, FF)

Multi-corner timing analysis is used to verify circuit performance under different manufacturing and environmental conditions. Since real chips are affected by variations in process, voltage, and temperature (PVT), timing must be checked across multiple corners.

## Concept

Different corners represent different operating conditions:

- Process variation (fast/slow transistors)  
- Voltage variation  
- Temperature variation  

STA is run for all corners to ensure reliable operation.


## Types of Corners

### 1. TT (Typical-Typical)
- Normal operating condition  
- Typical process, voltage, and temperature  

## Used for general timing analysis

### 2. SS (Slow-Slow)
- Slow transistors  
- Higher delay (worst-case for setup)


## Used to check setup violations

### 3. FF (Fast-Fast)
- Fast transistors  
- Lower delay (worst-case for hold)

## Used to check hold violations


---

## Comparison
```
| Corner | Speed  | Delay  |     Used For     |
|--------|--------|--------|------------------|
| TT     | Normal | Medium | Typical analysis |
| SS     | Slow   | High   | Setup check      |
| FF     | Fast   | Low    | Hold check       |
```

## Library Usage

Different `.lib` files are used for each corner:

```bash
sky130_fd_sc_hd__tt_025C_1v80.lib   # Typical
sky130_fd_sc_hd__ss_025C_1v60.lib   # Slow
sky130_fd_sc_hd__ff_025C_1v95.lib   # Fast
```





