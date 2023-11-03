# Overview of Repo
This repository is your guide to successfully completing RTL (Register-Transfer Level) and GLS (Gate-Level Simulation) for a Interrupt Controller design model. This project will help you gain hands-on experience with digital logic design and simulation.


# Interrupt Controller

It is a hardware component responsible for managing and prioritizing interrupt requests in a digital system. The interrupt controller interacts with a processor and peripheral devices to handle interrupt-driven events in a systematic manner.

The code defines an interrupt controller module with a finite state machine that manages interrupt requests, prioritizes them, communicates with the processor, and sends interrupt-related information on a bidirectional bus. The controller can operate in either polling mode or priority mode based on external commands. It's a fundamental component for handling interrupts in digital systems.
<details>
  <summary>RTL And GLS </summary>
  <br>


 
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

With the Rtl And Gls Output we can confirm that they both match.
Hence No Gls Mismatch.
</details>


<details>
  <summary>PD </summary>
  <br>

![1](https://github.com/kamildamudi21/pes_ic/assets/141449459/a08c1a8c-4c25-4c2b-b2ab-8bef5e492004)
![2](https://github.com/kamildamudi21/pes_ic/assets/141449459/3e808b8a-0115-49a7-9fcb-ec7f54009841)
![3](https://github.com/kamildamudi21/pes_ic/assets/141449459/9c352c46-1396-401f-ac8f-309e4024ccf2)
![4](https://github.com/kamildamudi21/pes_ic/assets/141449459/0fcea0d9-6784-4f5b-83fa-d25943d93d25)
![5](https://github.com/kamildamudi21/pes_ic/assets/141449459/3f388611-9931-4453-abc1-2b24e5246f46)
![6a](https://github.com/kamildamudi21/pes_ic/assets/141449459/2503d12c-c7a8-40df-bbcd-7ba9f9dac49b)
![6b](https://github.com/kamildamudi21/pes_ic/assets/141449459/993d75b6-f920-483d-b280-7328c36a4a5c)
![7](https://github.com/kamildamudi21/pes_ic/assets/141449459/f2c71d88-7e6a-44a6-aedd-9f3e4a338fcb)
![8(floorplan)](https://github.com/kamildamudi21/pes_ic/assets/141449459/4d198a02-9162-4070-b228-2be102cd4343)
![8(floorplan_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/c000f336-09d7-4282-ad06-07731ccbd6c1)
![9](https://github.com/kamildamudi21/pes_ic/assets/141449459/25fda90e-1ba0-421c-aeb8-9e4f7329820e)
![10(place)](https://github.com/kamildamudi21/pes_ic/assets/141449459/8004b617-e885-4a08-b28a-699d1c9bb119)
![10(place_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/4890e830-d93f-4c0e-b030-a9d30df23ca6)
![11](https://github.com/kamildamudi21/pes_ic/assets/141449459/f0c41d11-9204-4fdf-8502-2ef806c806de)
![12a](https://github.com/kamildamudi21/pes_ic/assets/141449459/435fcfdf-9791-4b3f-904d-1cb70547d0a7)
![12b](https://github.com/kamildamudi21/pes_ic/assets/141449459/10ebe4c9-0830-433e-87c0-168b8ba7b000)
![12c](https://github.com/kamildamudi21/pes_ic/assets/141449459/4c178cfb-1ce3-45de-a3bb-7315a0a64532)
![12d](https://github.com/kamildamudi21/pes_ic/assets/141449459/30e78019-0b60-49ef-ad78-884313ba5723)
![13](https://github.com/kamildamudi21/pes_ic/assets/141449459/91290516-6bde-43ed-a303-961a4c1be673)
![14(routing)](https://github.com/kamildamudi21/pes_ic/assets/141449459/b341ff3e-29e9-4d28-9138-8ed83a150892)
![14(routing_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/9e3259a6-88e2-4710-a9c2-e77ec57749c7)
![15a](https://github.com/kamildamudi21/pes_ic/assets/141449459/613dbebc-4db8-47a5-8bf2-bc6225ab6d3f)




</details>



