# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

1.Code Overview: Understand the Verilog module ripple_counter, which includes clock (clk) and reset (rst) inputs, and a 4-bit output count. The counter increments on each positive clock edge unless reset is asserted, resetting the count to 0.

2.Simulation Preparation: Use a Verilog simulator (e.g., ModelSim) and write a testbench module to apply clock and reset signals while monitoring the counter output.

3.Testbench Implementation: Instantiate the ripple_counter module in the testbench, generate clock and reset signals, apply them to the counter module, and observe the count output.

4.Simulation Execution: Compile both the counter module and the testbench, simulate the design, and verify that the counter counts from 0 to 15 (binary 1111) and resets to 0 when the reset signal is activated.

5.Verification and Debugging: Analyze timing diagrams to ensure proper counter behavior, debug any encountered issues during simulation, and make necessary modifications to the design for optimal functionality


**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by: Vaishnavi S.A
 RegisterNumber: 212223220119
 
*/
```
    module program12 (
        input clk,     
        input reset,  
        output [3:0] q 
    );
        
        reg [3:0] q_int;

        
        assign q = q_int;

        always @(posedge clk or posedge reset) begin
            if (reset) 
                q_int[0] <= 1'b0; 
            else 
                q_int[0] <= ~q_int[0]; 
       end

        // Generate the other flip-flops based on the output of the previous one
        genvar i;
        generate
            for (i = 1; i < 4; i = i + 1) begin : ripple
                always @(posedge q_int[i-1] or posedge reset) begin
                    if (reset) 
                        q_int[i] <= 1'b0; 
                    else 
                        q_int[i] <= ~q_int[i]; 
                end
            end
        endgenerate
    endmodule
```

**RTL LOGIC FOR 4 Bit Ripple Counter**

![397904820-e75b91b0-e4fc-4c5f-a8ab-1b0a4fb5abd9](https://github.com/user-attachments/assets/01467448-3848-47f1-81bc-a915f62a47d6)


**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![397906640-d33a16da-aa0f-42dd-a215-07edc8196410](https://github.com/user-attachments/assets/e7d81479-28c0-42cf-abae-8476bda8c0ce)


**RESULTS**

Thus the 4 Bit Ripple Counter is implemented using verilog and validated their functionality using their functional tables
