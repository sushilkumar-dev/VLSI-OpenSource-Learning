# 1.5 Simulation using Icarus Verilog

## Basic Concepts

### 1. What is Icarus Verilog?
- An open-source **Verilog compiler and simulator**
- Used to **compile and execute** Verilog code

---

### 2. Compilation
- Converts Verilog files into executable simulation file

```bash
iverilog and.v tb.v
```

### 3. Running Simulation
* Executes compiled design
```
vvp a.out
```

### 4. Output File Generation
* Generates waveform file ```(.vcd)``` for analysis
```
$dumpfile("wave.vcd");
$dumpvars(0, tb);
```

### 5. Viewing Results
* Output values can be seen in terminal or waveform viewer
```
$monitor("a=%b b=%b y=%b", a, b, y);
```

### 6. Multiple File Compilation
* Compile multiple modules together
```
iverilog design.v tb.v
```

### 7. Specify Output File Name
```
iverilog -o sim.out and.v tb.v
vvp sim.out
```

### 8. Debugging Errors
* Syntax errors shown during compilation
```
iverilog and.v
```

### 9. Simulation Time Control
* Controlled using delays ```#``` in testbench
```
#10 a = 1;
```

### 10. Complete Flow
```
iverilog and.v tb.v
vvp a.out
gtkwave wave.vcd
```
