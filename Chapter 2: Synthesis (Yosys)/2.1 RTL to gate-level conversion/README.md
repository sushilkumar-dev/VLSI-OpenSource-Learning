# Chapter 2: Synthesis (Yosys)

Synthesis is the process of converting a high-level RTL design written in Verilog into a gate-level netlist using standard cells from a technology library. In this stage, the design is optimized for area, timing, and performance, similar to what tools like Cadence Genus do.

---

### 2.1 RTL to Gate-Level Conversion

RTL (Register Transfer Level) describes the behavior of a circuit, while gate-level represents the actual hardware implementation using logic gates. During synthesis, tools convert RTL code into a network of logic gates.

```tcl
read_verilog and.v
synth
```

### 2.2 Technology Mapping (.lib)

Technology mapping maps generic logic gates to real standard cells defined in a .lib file (like Sky130 library). This step ensures the design is compatible with fabrication technology.

```
abc -liberty sky130_fd_sc_hd__tt_025C_1v80.lib
```

































