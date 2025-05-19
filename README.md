# RAM-DESIGN

COMPANY :CODTECH IT SOLUTIONS

NAME :B.SAISRIMA

INTERN ID :CT04DM37

DOMAIN : VLSI

DURATION : 4 WEEKS

MENTOR : NEELA SANTHOSH

**DESCRIPTION** :Design and Implementation of a Simple Synchronous RAM Module
The purpose of this project was to design, implement, and simulate a simple synchronous RAM (Random Access Memory) module that supports both read and write operations. RAM is a fundamental component of any computing system, used for storing and retrieving data dynamically during program execution. The RAM module in this project was designed to operate synchronously with a clock signal, meaning all memory access operations are controlled based on clock cycles, ensuring predictable and reliable data handling.

1. RAM Architecture and Functional Requirements
The RAM module was designed with the following specifications:

Word Width: 8 bits per memory location

Address Width: 4 bits, allowing access to 16 memory locations (2⁴ = 16)
Total Memory Size: 16 x 8 bits = 128 bits

Synchronous Operation: All read and write operations are triggered on the rising edge of the clock

Inputs:

clk: Clock signal

we: Write enable (1 for write, 0 for read)

addr: 4-bit address input

din: 8-bit data input (used during write)

Output:

dout: 8-bit data output (used during read)

How It Performs
Clocked Behavior: All memory actions occur on the rising edge of the clock (posedge clk).

Write:

At time 10 ns: we = 1, address = 2, din = 0xA5. Value 0xA5 is written to address 2.

At time 20 ns: we = 1, address = 4, din = 0x3C. Value 0x3C is written to address 4.

Read:

At time 30 ns: we = 0, address = 2. Value at address 2 (0xA5) is output on dout.

At time 40 ns: address = 4. Value at address 4 (0x3C) is output on dout.

Simulation confirms correct read/write operations synchronized with the clock. Data is stored and retrieved exactly as expected, validating RAM functionality.
// simple_sync_ram.v
module simple_sync_ram (
    input clk,
    input we,
    input [3:0] addr,
    input [7:0] din,
    output reg [7:0] dout
);

    reg [7:0] memory [0:15]; // 16 x 8-bit memory locations

    always @(posedge clk) begin
        if (we) begin
            memory[addr] <= din;    // Write operation on rising edge
        end
        dout <= memory[addr];       // Read operation on rising edge
    end

endmodule

The design of a simple synchronous RAM module provided practical experience with memory modeling, clock synchronization, and hardware description languages. The project clearly demonstrated how RAM can be built from register arrays and controlled using a clock signal. The write-enable signal was used effectively to manage data storage, and the read functionality was verified through simulation.

This module can be extended in the future to support:

Larger address widths

Asynchronous reads

Memory initialization via external file

Byte or word enable features

This RAM block can be easily integrated into a processor datapath or used in FPGA projects for embedded computing.
