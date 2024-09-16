
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

    

## Design Preparation Steps



```bash
cd Desktop/work/tool/openlane_working_dir/openlane
docker
./flow.tcl -interactive
```
    
## Design Preparation Steps

Getting start with openlane interactive 

Step 1 

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```

Step 2

```bash
  docker
```

Step 3

```bash
  ./flow interactive
```

Step 4

```bash
  prep -design picorv32a
```
![Screenshot from 2024-09-15 16-59-15](https://github.com/user-attachments/assets/8a79ab4a-1497-4a5e-acc7-a4b73778b8d6)


![Screenshot from 2024-09-15 11-18-26 - 1](https://github.com/user-attachments/assets/1dfaba9e-c3ca-4f75-adf4-313802ce9b90)


Step 5

```bash
  run_synthesis
```

![Screenshot from 2024-09-15 11-34-26](https://github.com/user-attachments/assets/2df618ab-f2f7-4402-b5a0-e5279980762c)

### Results
![Screenshot from 2024-09-15 11-41-44](https://github.com/user-attachments/assets/00cd68e7-d065-413d-80b2-ff4f311413ee)

![Screenshot from 2024-09-15 11-44-40](https://github.com/user-attachments/assets/633a0cf9-ce3c-406b-bebb-a020acc91b72)

![Screenshot from 2024-09-15 12-02-35](https://github.com/user-attachments/assets/28f3bc2a-df9c-4f9f-9355-5c2604898b92)

## Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells

### SKY130_D2_SK1 - Chip Floor planning considerations

### Floorplan files and steps to view floorplan


```bash
 run_floorplan
 cd Desktop/work/tool/openlane_working_dir/openlane/configuration
```

steps for floorpaln

```bash
  run_floorplan
```
![Screenshot from 2024-09-15 12-11-28](https://github.com/user-attachments/assets/4c4a2c39-bedc-4dae-bb7c-e1b509b83f82)

![Screenshot from 2024-09-15 12-12-11](https://github.com/user-attachments/assets/7cff88ad-cfa5-4698-9f08-9390de21a3b6)

### checking results in directory

![Screenshot from 2024-09-15 12-15-23](https://github.com/user-attachments/assets/b3ac3cbc-e7d2-43de-8594-0091e20c3889)

## Results for seeing the floorplan 

Change the directory

```bash
cd Desktop/work/tool/openlane_working_dir/openlane/designs/picorv32a/08-09_14-03/results/floorplan
```

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```



![Screenshot from 2024-09-15 13-51-06](https://github.com/user-attachments/assets/b54448e2-8f90-458e-a535-205005172029)

![Screenshot from 2024-09-15 13-51-19](https://github.com/user-attachments/assets/79ad2e81-fb17-4b06-a788-369a328f426b)

![Screenshot from 2024-09-15 17-19-31 (1)](https://github.com/user-attachments/assets/e1500972-6f0e-4012-b7c6-e41a76ec20a8)

![Screenshot from 2024-09-15 17-22-16 (1)](https://github.com/user-attachments/assets/591d7ebd-8879-406b-b916-c429149e5e5b)

### Placement 
 Optimize placement using estimated wire-length and capacitance

 ```bash
  run_placement
```
![Screenshot from 2024-09-15 17-27-44](https://github.com/user-attachments/assets/024a1b44-5300-4184-8c9f-20e6a2a70304)

![Screenshot from 2024-09-15 17-28-05](https://github.com/user-attachments/assets/ac988eee-9959-467f-86e0-8f8ee95e79e9)


Change the directory

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/09-09_06-53/results/placement/
```

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```


![Screenshot from 2024-09-15 17-38-15](https://github.com/user-attachments/assets/4091e2c4-9163-4e38-be6c-eb7c9306cb89)

![Screenshot from 2024-09-15 17-37-50](https://github.com/user-attachments/assets/b17e4e00-f49e-4602-b5ed-4ffe02ce16f7)

# Sky130 Day 3 - Design library cell using Magic Layout and ngspice characterization
Cloning custom inverter standard cell design repository
```bash
 git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

![Screenshot from 2024-09-08 17-52-22](https://github.com/user-attachments/assets/8dd5b4d6-1c62-4587-8798-f749dd6f9f48)
![Screenshot from 2024-09-08 18-05-05](https://github.com/user-attachments/assets/1ddd579d-2a35-4b50-88f6-6596f6188b63)


![Screenshot from 2024-09-08 18-07-43](https://github.com/user-attachments/assets/0a7da060-1ef3-42f2-b740-80ec0bca8336)

![Screenshot from 2024-09-08 18-19-04](https://github.com/user-attachments/assets/934ea196-e7b1-45ed-b42a-2ffc6fb0d9cd)

![Screenshot from 2024-09-08 18-07-46](https://github.com/user-attachments/assets/8b650bc9-0325-4eb1-95f8-d71c32665df9)

## Extracting CMOS inverter to SPICE characterization
line code for spice
```bash
 pwd
 extract all
 ext2spice cthresh 0 rthresh 0
 ext2spice
```

![WhatsApp Image 2024-09-15 at 6 41 34 PM](https://github.com/user-attachments/assets/153ef8a5-8a57-464a-beb7-e9ff15c975a9)

![WhatsApp Image 2024-09-15 at 6 41 53 PM](https://github.com/user-attachments/assets/650889ff-f858-44e6-ace6-063ce0794773)

Opening SPICE extracted file
```bash
  vim sky130_inv.spice
```

![WhatsApp Image 2024-09-15 at 8 55 32 PM](https://github.com/user-attachments/assets/e4bd7c52-5ca8-44db-8942-f4d2a0fb57ed)

ploting the SPICE
```bash
 ngspice sky130_inv.spice
 plot y vs time a
```
![WhatsApp Image 2024-09-15 at 6 42 03 PM](https://github.com/user-attachments/assets/44cb0a55-260d-422c-b4ef-e54e4604ea02)
![WhatsApp Image 2024-09-15 at 6 42 18 PM](https://github.com/user-attachments/assets/2ec0a303-dfd0-46e5-a5b3-3dc710b08cf5)



### SKY_L3 - Lab introduction to Magic tool options and DRC rules

```bash
 wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
 tar xfz drc_tests.tgz
 cd drc_tests
```
![WhatsApp Image 2024-09-15 at 9 38 47 PM](https://github.com/user-attachments/assets/54c73ab9-6bd6-400b-abc9-e21a042e936e)

To view .magicrc file
```bash
 gvim .magicrc
```
![WhatsApp Image 2024-09-16 at 9 41 22 AM](https://github.com/user-attachments/assets/bde6e5a3-19c4-449a-947b-fc86dc1aca62)

### Result

![WhatsApp Image 2024-09-16 at 9 41 22 AM (1)](https://github.com/user-attachments/assets/3d8aa4b6-0070-4412-b78b-75303c431864)
![WhatsApp Image 2024-09-16 at 9 41 22 AM (2)](https://github.com/user-attachments/assets/cae80969-1894-4722-b6af-e79b8d3d7aba)

DRC rule for poly.9 in skywater130A pdk

![WhatsApp Image 2024-09-16 at 9 41 22 AM (3)](https://github.com/user-attachments/assets/1d076ff0-b333-4b58-a80d-01c9bd9fe9f3)
![WhatsApp Image 2024-09-16 at 9 41 22 AM (4)](https://github.com/user-attachments/assets/17356a7a-7a68-4276-aec7-80c3a3c8a1c6)
![WhatsApp Image 2024-09-16 at 9 41 22 AM (5)](https://github.com/user-attachments/assets/28556827-5632-4cfe-8b28-994b30b6ea74)


```bash
vi sky130A.tech
```
![WhatsApp Image 2024-09-16 at 11 15 04 AM](https://github.com/user-attachments/assets/01960d17-29dd-4e33-b340-b27118fb35f6)
![WhatsApp Image 2024-09-16 at 11 15 04 AM (1)](https://github.com/user-attachments/assets/e2c76095-a42a-4e81-8fbd-81282fb768df)

## Sky130 Day 4 - Pre-layout timing analysis and importance of good clock tree
SKY_L1 - Lab steps to convert grid info to track info
A requirement for ports as specified in tracks.info is that they should be at the intersection of horizontal and vertical tracks. The CMOS Inverter ports A and Y are on the li1 layer. It must be ensured that they're on the intersection of horizontal and vertical tracks. We access the tracks.info
```bash
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag &
```
![WhatsApp Image 2024-09-16 at 11 22 45 AM](https://github.com/user-attachments/assets/230f2079-46df-41bb-84b2-5efd55035935)
![WhatsApp Image 2024-09-16 at 11 22 45 AM (1)](https://github.com/user-attachments/assets/a767aed4-0093-4fd1-80d5-ce57233589e3)

To set the grid values in Magic, you can use the grid command.

```bash
help grid
grid 0.46um 0.34um 0.23um 0.17um
```
Saving the layout

```bash
save sky130_vsdinv.mag
magic -T sky130A.tech sky130_vsdinv.mag &
lef write
```

### Results
![WhatsApp Image 2024-09-16 at 11 22 46 AM](https://github.com/user-attachments/assets/fd305b8b-e770-4a80-b253-64fada66fc84)
![WhatsApp Image 2024-09-16 at 11 22 46 AM (1)](https://github.com/user-attachments/assets/16abc80c-90ae-434d-b808-846efcb2e87c)
![WhatsApp Image 2024-09-16 at 11 22 49 AM](https://github.com/user-attachments/assets/26fe86ff-bbc1-4da8-9483-5cba12860258)

## SKY_L3 - Introduction to timing libs and steps to include new cell in synthesis
## Copying lef and LIB files to picorv32a

Copying LEF and Required LIB Files to picorv32a Design's src Directory

Step 1 

```bash
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Step 2

```bash
 ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Step 3

```bash
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Step 4

```bash
  ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```


![whatsapp](https://github.com/user-attachments/assets/5837cfd3-4f01-4ae8-995a-85cb847c1fa5)



