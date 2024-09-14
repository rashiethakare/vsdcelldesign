
#  Digital VLSI SoC Design and Planning (Picorv32)


## DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK

OpenLANE software 



OpenLane is an open-source, automated, and customizable physical design flow for digital integrated circuits (ICs). It's developed as part of the OpenROAD project and is specifically aimed at supporting open-source hardware design. OpenLane is widely used for creating chip designs from high-level hardware description languages (HDLs) such as Verilog down to a layout ready for fabrication.

### Key Features:
1. **Front-to-back flow**: OpenLane covers the complete RTL-to-GDSII flow, starting from RTL synthesis through placement, routing, and final layout (GDSII).
2. **Compatibility with OpenROAD Tools**: It is designed to integrate seamlessly with other tools in the OpenROAD suite, such as OpenSTA (Static Timing Analysis), TritonRoute (detailed router), and Yosys (RTL synthesis).
3. **Automated**: OpenLane focuses on automation, requiring minimal manual intervention once you define the design constraints and configuration files.
4. **Customizable**: Users can fine-tune the flow to their design’s needs by customizing scripts and parameters.
5. **FreePDK45 and SkyWater 130nm PDK Support**: OpenLane supports standard open-source process design kits (PDKs) such as SkyWater’s 130nm technology and FreePDK45.
6. **Open-source**: Both the tools and the flow are open-source, making it accessible for educational purposes, research, or open-source silicon projects.

### Typical Flow:
1. **RTL Synthesis**: Translates the RTL design (typically in Verilog) into a gate-level netlist.
2. **Floorplanning**: Determines the placement of components on the chip to optimize area and power.
3. **Placement**: Places the standard cells onto the floorplan.
4. **Clock Tree Synthesis (CTS)**: Ensures that clock signals reach all parts of the chip in a synchronized manner.
5. **Routing**: Connects all placed cells to satisfy the netlist and meet timing constraints.
6. **Design Rule Checking (DRC) and Layout vs. Schematic (LVS)**: Ensures that the layout matches the schematic and complies with the fabrication rules.

### Use Cases:
- Educational IC design projects
- Research in physical design and VLSI
- Open-source hardware development

### Supported Tools:
- **Yosys**: RTL synthesis
- **OpenSTA**: Static Timing Analysis
- **TritonRoute**: Detailed routing
- **Magic**: Layout visualization
- **Klayout**: GDSII viewer

This toolchain is popular among chip designers who prefer an open-source approach for silicon development.

![Screenshot 2024-09-14 214119](https://github.com/user-attachments/assets/8b429601-b477-42f5-b707-4ba6014a4803)

    
