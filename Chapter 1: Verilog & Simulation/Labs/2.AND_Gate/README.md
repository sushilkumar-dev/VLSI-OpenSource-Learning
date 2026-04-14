# AND Gate

## Objective
To design and simulate an AND gate using Verilog.

## Description
The AND gate outputs high (1) only when both inputs are high.

## Simulation Steps
iverilog and.v tb_and.v
vvp a.out
gtkwave wave.vcd

## Expected Output
```
| a | b | y |
| - | - | - |
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |
```
## Output
Waveform verified using GTKWave.

<img width="600" height="600" alt="Screenshot from 2026-04-14 11-55-12" src="https://github.com/user-attachments/assets/374f4223-7556-4b1c-9319-e23a8e6a21f7" />
