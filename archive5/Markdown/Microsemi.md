#

- Worked on development of test structures and designs using Microsemi's design software, Libero, to assess and characterize Microsemi FPGA products that went to market.
- Specifically, characterized the Mathblock component of Microsemi's G5 FPGA product as well as performance-related AC tests on other combinatorial and sequential elements found in the FPGA.
    - Example components include look-up tables, carry chains, digital I/O's.
    - Mainly characterized in terms of maximum frequency.
    - Tested chains on different corners of the FPGA fabric.
    - AC characterization was done on Verigy 93k tester offsite using test vectors generated on site.
- Inside Libero, I created Verilog test structures, making use of JTAG to read input from test programs created using a company code.
    - Also used Libero-specific SmartTime software to enforce timing constraints in my designs and check for any violations.
- Created testbenches and wave.do files to perform simulations of the test design using the ModelSim environment.
    - The wave.do files mimicked the signals normally fed into the system by the test programs.
- Additionally assisted with the Product Engineering team in programming devices pre and post burn-in.
- Wrote sections of the characterization report found in the official product manual.
