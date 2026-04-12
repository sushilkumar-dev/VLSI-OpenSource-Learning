# 1.4 Testbench Development

## Basic Concepts

### 1. What is a Testbench?
- A testbench is used to **verify the functionality** of a design.
- It **applies inputs** and **observes outputs**.

```verilog
module tb;
endmodule
```

### 2. No Ports in Testbench
* Testbench does not have input/output ports.
```
module tb;
// no ports
endmodule
```

### 3. DUT Instantiation (Design Under Test)
* Connect the design module inside testbench.
```
and_gate uut (
    .a(a),
    .b(b),
    .y(y)
);
```

### 4. Stimulus Generation
* Apply different input values using initial block.
```
initial begin
    a = 0; b = 0;
    #10 a = 1; b = 0;
end
```

### 5. Time Delay
* ```#``` is used to delay signal changes.
```#10 a = 1;```

### 6. Dump File (for GTKWave)
* Used to generate waveform file.
```
$dumpfile("wave.vcd");
$dumpvars(0, tb);
```

### 7. Monitoring Signals
* Print values during simulation.
```
$monitor("a=%b b=%b y=%b", a, b, y);
```

### 8. Loop-based Testing
* Automate test cases using loops.
```
integer i;
initial begin
    for(i=0; i<4; i=i+1)
        {a,b} = i;
end
```

### 9. Finish Simulation
* Stops simulation.
```
$finish;
```

### 10. Complete Example
```
module tb;

reg a, b;
wire y;

and_gate uut (
    .a(a),
    .b(b),
    .y(y)
);

initial begin
    $dumpfile("wave.vcd");
    $dumpvars(0, tb);

    a=0; b=0;
    #10 a=0; b=1;
    #10 a=1; b=0;
    #10 a=1; b=1;

    #10 $finish;
end

endmodule
```
