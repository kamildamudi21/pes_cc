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

- First create a folder in you Openlane/design directory and save your design there.
![1](https://github.com/kamildamudi21/pes_ic/assets/141449459/a08c1a8c-4c25-4c2b-b2ab-8bef5e492004)

- Then create a folder named 'src' and save the main verilog code in that folder too and also save it outside the folder as well , with the verilog code also save the
```
sky130_fd_sc_hd__fast.lib
sky130_fd_sc_hd__slow.lib
sky130_fd_sc_hd__typical.lib
```
- create a config.json file outside your src folder.
- all the files are present at the top

![3](https://github.com/kamildamudi21/pes_ic/assets/141449459/57cc6bd6-85ca-4f1a-8b4a-16a7d67a681e)

### Interactive OpenLane flow
Open terminal in home directory and then type the following:



cd OpenLane/ 
sudo make mount 
```
./flow.tcl -interactive
package require openlane 0.9
prep -design pes_ic
```

![4](https://github.com/kamildamudi21/pes_ic/assets/141449459/fa2a3310-37a3-429f-93af-6d75f6520641)


```
run_synthesis
run_floorplan
run_placement
run_cts
run_routing
run_magic
run_magic_spice_export
run_magic_drc
run_netgen
run_magic_antenna_check
```


## Synthesis stage:
Synthesis is a fundamental stage in the digital design flow. It takes an abstract hardware description and generates a netlist consisting of logical gates and flip-flops that represent the desired functionality of the design.

![5](https://github.com/kamildamudi21/pes_ic/assets/141449459/b6df0ab6-cff5-4ad7-9634-253398a653e9)



- Area report

![6a](https://github.com/kamildamudi21/pes_ic/assets/141449459/d1391d9a-280a-442f-bd7b-519244a410a8)
![6b](https://github.com/kamildamudi21/pes_ic/assets/141449459/6ea396a0-d4f5-49cd-b451-45a9c0c5e2e4)


## Floorplan stage:

The floorplan stage in digital integrated circuit design involves creating a high-level layout for the chip, defining the core area, the locations of I/O pads, and other critical structures. It establishes the overall physical framework for the chip design and serves as a foundation for subsequent stages such as placement and routing. During the floorplan stage, designers make decisions about the chip's dimensions, aspect ratio, power grid, and other essential aspects to meet the project's requirements. The goal is to efficiently allocate space for various components while adhering to design constraints, ultimately ensuring that the chip will meet its performance, power, and area goals.

![7](https://github.com/kamildamudi21/pes_ic/assets/141449459/bcca33ec-95d4-4646-a54f-2011720fa6f3)


```
magic -T /home/kamild/OpenLane/pdk/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.nom.lef def pes_ic.def &
```

![8(floorplan)](https://github.com/kamildamudi21/pes_ic/assets/141449459/572d45a8-a5ba-431c-92b4-bfdba5f4af11)

- Floorplan Zoomed.
  
![8(floorplan_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/595d835a-74a3-43b9-9c18-4b9f58506f6c)

## Placement stage:

The placement stage in digital integrated circuit design involves determining the physical positions of synthesized logic cells on the chip's layout. This critical step aims to optimize the arrangement of cells to minimize wirelength, meet design constraints, and achieve desired performance. Placement typically involves global placement, which provides a rough layout, followed by legalization to ensure cells conform to design rules and spacing requirements. The outcome of this stage is a physical placement file that specifies the coordinates of each cell, serving as the basis for subsequent routing and design verification steps. Efficient placement is essential for optimizing area, power, and signal timing in the final chip design.

![9](https://github.com/kamildamudi21/pes_ic/assets/141449459/88e7c5f3-b6ac-4146-b92e-2aca83b4a454)

```
magic -T /home/kamild/OpenLane/pdk/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.nom.lef def pes_dff_async.def &
```

![10(place)](https://github.com/kamildamudi21/pes_ic/assets/141449459/be2e9d6a-9b16-4855-915a-93546a75497f)

- Placement Zoomed.

![10(place_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/2b6365a2-09c2-43db-b4e1-baddf261543e)


## Cts stage:



The Clock Tree Synthesis (CTS) phase's primary objective is to establish a clock distribution network guaranteeing dependable and synchronized clock signals for all the sequential components, such as flip-flops, within the chip. This phase encompasses the subsequent pivotal procedures:

- Buffer Insertion: In the CTS procedure, buffers are incorporated into the clock network to achieve uniform distribution of the clock signal. These buffers play a crucial role in mitigating clock skew, thereby ensuring simultaneous delivery of clock signals to all sections of the chip.

- Clock Tree Construction: The clock tree is built by linking the buffers in a hierarchical manner, extending from the global clock source (such as a PLL or external input) to the individual leaf-level cells across the entire chip.

- Skew Minimization: Within the CTS phase, the objective is to reduce clock skew, which represents the disparity in clock signal arrival times at various locations in the design. By minimizing skew, the aim is to guarantee that all registers observe the same clock edge concurrently, a critical requirement for the effective operation of the circuit.
- 
- Power Optimization: CTS also involves power optimization techniques to reduce dynamic and static power consumption in the clock distribution network.

- Constraints and Timing: It takes into consideration the design constraints related to clock paths, such as clock-to-q requirements, setup and hold times, and other timing considerations.

- Clock Gating: Clock gating cells may be inserted in the clock tree to save power when certain parts of the chip are not in use, and the clock can be temporarily disabled.


![11](https://github.com/kamildamudi21/pes_ic/assets/141449459/16de0272-59ac-408f-aa2a-94e6dfc9e457)
<br>
- report
  
![12a](https://github.com/kamildamudi21/pes_ic/assets/141449459/04e79663-59e1-486d-ad8b-94fa42dd0f5c)
![12b](https://github.com/kamildamudi21/pes_ic/assets/141449459/3b5118cb-f0c1-4690-9832-557b0b31fc8c)
![12c](https://github.com/kamildamudi21/pes_ic/assets/141449459/a1ee902f-0b99-40cf-9c48-6314665925df)
![12d](https://github.com/kamildamudi21/pes_ic/assets/141449459/c6ff5974-d64d-4d87-bdbf-6a9b3d2954d7)


## Routing stage:

- The routing stage is responsible for creating the physical wire connections between the placed cells on the chip layout. This involves determining the paths for signal wires, power distribution, and clock signals, while adhering to design rules, avoiding congestion, and optimizing for various factors such as wirelength, signal delay, and power consumption.

![13](https://github.com/kamildamudi21/pes_ic/assets/141449459/3e2bb2e4-75c1-46f8-9ea5-ae8d01078036)


```
magic -T /home/kamild/OpenLane/pdk/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.nom.lef def pes_dff_async.def &
```

![14(routing)](https://github.com/kamildamudi21/pes_ic/assets/141449459/0a7f19e7-3974-4618-bdc3-bb9b13a1bca7)

- router zoomed.
  
![14(routing_zoom)](https://github.com/kamildamudi21/pes_ic/assets/141449459/b10342b5-5a0e-4bc7-a5c2-cefda382f34b)


- Power report

![15a](https://github.com/kamildamudi21/pes_ic/assets/141449459/d0236f06-2eb1-4113-b111-0ae4c2eca86c)

</details>



