# 1.3 Sequential Logic Basics

## Basic Concepts

### 1. What is Sequential Logic?
- Output depends on **current inputs + previous state (memory)**
- Uses **clock signal**

```verilog
always @(posedge clk)
    q <= d;
```

### 2. Flip-Flop (D Flip-Flop)
* Stores 1-bit data
* Updates on clock edge
```
module dff(input clk, input d, output reg q);
always @(posedge clk)
    q <= d;
endmodule
```

### 3. Clock Signal
* Controls when data is updated
```always @(posedge clk)```

### 4. Reset Logic
* Initializes the circuit
```
always @(posedge clk or posedge rst) begin
    if (rst)
        q <= 0;
    else
        q <= d;
end
```

### 5. Registers
* Multi-bit storage elements
```reg [3:0] data;```

### 6. Blocking vs Non-Blocking
* Sequential logic uses non-blocking ```(<=)```
```q <= d;```

### 7. Edge Triggering
* Positive edge (posedge)
* Negative edge (negedge)
```always @(negedge clk)```

### 8. Finite State Machine (FSM)
* Used for control logic
```reg [1:0] state;```

### 9. Shift Register
* Data shifts on each clock
```
always @(posedge clk)
    q <= {q[2:0], d};
```

### 10. Counter Design
* Sequential counting logic
```
always @(posedge clk)
    count <= count + 1;
```

