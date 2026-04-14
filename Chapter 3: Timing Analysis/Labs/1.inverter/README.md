# Inverter Timing Analysis

## Objective
To perform static timing analysis (STA) on a CMOS inverter using OpenSTA.

## Description
The synthesized inverter netlist is analyzed to evaluate timing parameters such as delay and slack. Since the inverter is a combinational circuit, timing analysis focuses on path delay without sequential clock constraints.

## Files Used
- inverter_netlist.v → Gate-level netlist  
- inverter.sdc → Timing constraints  
- sta.tcl → STA script  
- report.txt → Timing report  

## Steps
opensta sta.tcl

## Output
- Analyzed signal delay  
- Observed slack values  
- Verified no timing violations  

## Conclusion
The inverter design meets timing requirements and operates correctly without any violations.
