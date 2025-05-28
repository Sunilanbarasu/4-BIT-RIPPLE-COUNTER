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



**PROGRAM**
```
module ripple_counter(
    input wire clk,        // Clock input
    input wire reset,      // Asynchronous reset
    output wire [3:0] q    // 4-bit output
);

    wire clk1, clk2, clk3;

    // First flip-flop (LSB)
    T_FF tff0 (
        .clk(clk),
        .reset(reset),
        .q(q[0]),
        .clk_out(clk1)
    );

    // Second flip-flop
    T_FF tff1 (
        .clk(clk1),
        .reset(reset),
        .q(q[1]),
        .clk_out(clk2)
    );

    // Third flip-flop
    T_FF tff2 (
        .clk(clk2),
        .reset(reset),
        .q(q[2]),
        .clk_out(clk3)
    );

    // Fourth flip-flop (MSB)
    T_FF tff3 (
        .clk(clk3),
        .reset(reset),
        .q(q[3]),
        .clk_out()
    );

endmodule

// Toggle Flip-Flop Module
module T_FF (
    input wire clk,
    input wire reset,
    output reg q,
    output wire clk_out
);
    assign clk_out = q;  // Output to next stage

    always @(negedge clk or posedge reset) begin
        if (reset)
            q <= 0;
        else
            q <= ~q;
    end
endmodule
```

 Developed by: RegisterNumber: 212224220113

**RTL LOGIC FOR 4 Bit Ripple Counter**
![ex12](https://github.com/user-attachments/assets/fa1d313d-52b8-4355-94fb-6b65d31b2e0a)

**DIGRAMS FOR 4 Bit Ripple Counter**
![image](https://github.com/user-attachments/assets/b3f38add-5241-4da2-9f47-da70f8e1cd3d)


**RESULTS**

Thus the 4 Bit Ripple Counter using verilog is implemented and their functionality using their functional tables is validated.
