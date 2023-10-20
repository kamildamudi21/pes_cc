# Overview of Repo
This repository is your guide to successfully completing RTL (Register-Transfer Level) and GLS (Gate-Level Simulation) for a Interrupt Controller design model. This project will help you gain hands-on experience with digital logic design and simulation.


# Interrupt Controller

It is a hardware component responsible for managing and prioritizing interrupt requests in a digital system. The interrupt controller interacts with a processor and peripheral devices to handle interrupt-driven events in a systematic manner.

The code defines an interrupt controller module with a finite state machine that manages interrupt requests, prioritizes them, communicates with the processor, and sends interrupt-related information on a bidirectional bus. The controller can operate in either polling mode or priority mode based on external commands. It's a fundamental component for handling interrupts in digital systems.

## RTL Simulation

It is an essential step in the process of designing and verifying digital hardware components, such as microprocessors, ASICs (Application-Specific Integrated Circuits), and FPGAs (Field-Programmable Gate Arrays).
We use Gtkwave to view the output.
![1gtk](https://github.com/kamildamudi21/pes_ic/assets/141449459/2c52f1dc-2664-4026-9f60-11b446efa3cb)

## RTL Synthesis
RTL synthesis optimizes the design for area, speed, and power consumption.
RTL synthesis performs timing analysis to ensure that the design meets its required performance criteria.

![2vcddump](https://github.com/kamildamudi21/pes_ic/assets/141449459/9a2252e0-070e-41ac-bac0-0b05f7a837c8)
![3abc](https://github.com/kamildamudi21/pes_ic/assets/141449459/aa9f6342-fca2-4b76-b83a-290e5e242be0)
![4synthesis](https://github.com/kamildamudi21/pes_ic/assets/141449459/2999a75a-598d-4ae6-b92d-6d0aa418dff4)

## GLS Synthesis

 This stage follows RTL synthesis and involves converting the logical description of the design into a physical layout that can be manufactured.
  ```
  iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v pes_ic_net.v tb_pes_ic.v
  ./a.out
  gtkwave tb_pes_ic.vcd

  ```

![3gdsterminal](https://github.com/kamildamudi21/pes_ic/assets/141449459/748c49a4-7f28-4762-aa45-fe84c42ad38f)

![4gds](https://github.com/kamildamudi21/pes_ic/assets/141449459/ec888779-40e7-487e-8544-021927dec42e)

# Conclusion

With the Rtl And Gds Output we can confirm that they both match.
Hence No Gls Mismatch.






