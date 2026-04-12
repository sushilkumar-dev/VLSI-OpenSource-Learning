# 1.2 Combinational Logic Design

## Basic Concepts

### 1. What is Combinational Logic?
- Output depends only on current inputs (no memory)
- No clock involved

---

### 2. Basic Logic Gates
- AND, OR, NOT, NAND, NOR, XOR
- Implemented using `assign`

```verilog
assign y = a & b;   // AND
assign y = a | b;   // OR
assign y = ~a;      // NOT
```

### 3. Boolean Expressions
* Digital circuits are represented using Boolean equations

```assign y = (a & b) | (~c);```

### 4. Truth Table Design
* Define output for all input combinations
```
a	b	y
0	0	0
0	1	0
1	0	0
1	1	1
```

### 5. Conditional Statements (Combinational)

```assign y = (sel) ? a : b;```
* This is a ternary (conditional) operator in Verilog.
* It works like an if-else statement.

* Equivalent Logic
```
if (sel)
    y = a;
else
    y = b;
```

### 6. Combinational Always Block
```
always @(*) begin
    y = a & b;
end
```

### 7. Case Statement
```
always @(*) begin
    case(sel)
        2'b00: y = a;
        2'b01: y = b;
        default: y = 0;
    endcase
end
```

### 8. Multiplexer Design
```
module mux(input a, input b, input sel, output y);
assign y = sel ? b : a;
endmodule
```

### 9. Avoiding Latches
* Always assign all outputs in every condition
```
always @(*) begin
    if(a)
        y = b;
    else
        y = 0;
end
```

### 10. Priority Logic (if-else)
```
module priority(input a, input b, input c, output reg y);
always @(*) begin
    if(a)
        y = b;
    else if(c)
        y = 1;
    else
        y = 0;
end
endmodule
```









