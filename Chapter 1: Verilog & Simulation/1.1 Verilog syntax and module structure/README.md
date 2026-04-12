# 1.1 Verilog Syntax & Module Structure

## Basic Concepts

### 1. Module Definition
- A module is the basic building block in Verilog.
- It defines inputs, outputs, and internal logic.

```verilog
module inverter (
    input a,
    output y
);

assign y = ~a;

endmodule 
```

### 2. Data Types
* ```wire``` → used for connections (combinational logic) </br>
* ```reg``` → used in procedural blocks (always)
```
wire a;
reg b;
```

### 3. Continuous Assignment
* Used for combinational logic using ```assign```.
```
assign y = a & b;
```

### 4. Operators
Arithmetic: ```+ - * /``` </br>
Logical: ```&& || !``` </br>
Bitwise: ```& | ^ ~``` </br>
Relational: ```== != > <``` </br>

### 5. Module Instantiation
* Reusing a module inside another module.
```
inverter u1 (
    .a(a),
    .y(y)
);
```

### 6. Always Block
* Used for sequential and behavioral modeling.
```
always @(posedge clk) begin
    q <= d;
end
```

### 7. Blocking vs Non-Blocking
```=``` → blocking (sequential execution) </br>
```<=``` → non-blocking (parallel execution)

### 8. Sensitivity List
* Defines when ```always``` block executes.
```
always @(a or b)
or
always @(*)
```

### 9. Parameterization
* Used to create flexible designs.
```
module adder #(parameter N = 4) (
    input [N-1:0] a, b,
    output [N-1:0] sum
);
```


### 10. Generate Block
* Used for scalable hardware design.
```
genvar i;
generate
for(i=0; i<4; i=i+1) begin
    assign y[i] = a[i] & b[i];
end
endgenerate
```





















  
