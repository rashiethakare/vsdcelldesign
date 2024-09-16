
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

![Screenshot from 2024-09-16 13-35-53](https://github.com/user-attachments/assets/4e88eaad-e06c-409b-9bb9-35297bbdea6b)

### Editing the config.tcl and adding new lef file
## LIB Files adding steps

this are adding in config.tcl Files

Step 1 

```bash
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

```

Step 2

```bash
 set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
```

Step 3

```bash
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
```

Step 4

```bash
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
```
## Custom LEF File
```bash
set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

![WhatsApp Image 2024-09-16 at 8 55 50 PM](https://github.com/user-attachments/assets/e67d887a-aa20-402d-a992-646155247747)

![WhatsApp Image 2024-09-16 at 8 55 50 PM (1)](https://github.com/user-attachments/assets/99b5ed6b-68f4-4936-b016-1dc2134d3a26)


# Invoking OpenLANE FLOW

this are adding in config.tcl Files

Step 1 

change the directory
```bash
cd Desktop/work/tools/openlane_working_dir/openlane
```

Step 2

```bash
 docker
```

Step 3

```bash
./flow.tcl -interactive
```

Step 4

```bash
package require openlane 0.9
```

Step 5

```bash
prep -design picorv32a
```

Step 6

```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```
Step 7

```bash
run_synthesis
```

![WhatsApp Image 2024-09-16 at 9 27 51 PM](https://github.com/user-attachments/assets/84fdab73-21e8-4f0d-8569-9f2d67e8f991)

![WhatsApp Image 2024-09-16 at 9 27 51 PM](https://github.com/user-attachments/assets/cf348915-2342-4ab2-81ed-f13be01288ff)

![WhatsApp Image 2024-09-16 at 9 27 51 PM (1)](https://github.com/user-attachments/assets/c57f3b69-7373-4b11-92e9-411e827cd3b4)
![WhatsApp Image 2024-09-16 at 9 27 54 PM](https://github.com/user-attachments/assets/435ddf4c-c986-4745-a755-f90c93118f65)

## Updating Design Variables, Including Custom LEF, and Running Synthesis for picorv32a


```bash
prep -design picorv32a -tag 15-09_05-48 -overwrite

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

echo $::env(SYNTH_STRATEGY)

set ::env(SYNTH_STRATEGY) "DELAY 3"

echo $::env(SYNTH_BUFFERING)

echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

echo $::env(SYNTH_DRIVING_CELL)

run_synthesis
```
![WhatsApp Image 2024-09-16 at 9 42 57 PM](https://github.com/user-attachments/assets/ef6c3021-7c43-4c65-a914-5916e2dcf9ed)
![WhatsApp Image 2024-09-16 at 9 42 57 PM (1)](https://github.com/user-attachments/assets/14660c47-53c2-4c8b-8ba8-59b1d68077ed)
![WhatsApp Image 2024-09-16 at 9 42 57 PM (2)](https://github.com/user-attachments/assets/4ada8b85-e462-4e08-bb56-647f5b093096)
![WhatsApp Image 2024-09-16 at 9 42 57 PM (3)](https://github.com/user-attachments/assets/7bab2d04-3e18-4a6a-b1ad-b603d9ee5344)
![WhatsApp Image 2024-09-16 at 9 42 58 PM](https://github.com/user-attachments/assets/07ad45a2-2a81-4dc9-913b-ef848e19b777)
## Running the Floorplan 

```bash
run_floorplan
```

![WhatsApp Image 2024-09-16 at 9 42 59 PM](https://github.com/user-attachments/assets/765797e2-4cfa-46d7-ba73-d67c4e5eb11e)

If getting error in floorplan running 

![WhatsApp Image 2024-09-16 at 9 43 00 PM](https://github.com/user-attachments/assets/c05cbc5b-7818-48e8-87c6-c67066eab731)

run this to get floorplan

```bash
init_floorplan
place_io
tap_decap_or
```
![WhatsApp Image 2024-09-16 at 9 43 01 PM](https://github.com/user-attachments/assets/a37cfd5a-764e-4d9c-8923-02f04eb9b19e)

![WhatsApp Image 2024-09-16 at 9 43 01 PM (1)](https://github.com/user-attachments/assets/436d5652-d6b4-4549-b9e6-303029345980)

![WhatsApp Image 2024-09-16 at 9 43 04 PM](https://github.com/user-attachments/assets/1b40034e-cd6b-47ce-ae95-8139cc5fb95b)

## NEXT running the placement 

```bash
run_placement 
```
![WhatsApp Image 2024-09-16 at 9 43 04 PM (1)](https://github.com/user-attachments/assets/60212505-8b5f-495e-9432-bf10f8dfcc80)

![WhatsApp Image 2024-09-16 at 9 43 04 PM (2)](https://github.com/user-attachments/assets/e9b5eddd-1242-4db7-b725-50992837dd4e)

moving to new terminal

```bash
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/09-09_06-53/results/placement/
```
seeing the placement

```bash
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

![WhatsApp Image 2024-09-16 at 9 43 04 PM (3)](https://github.com/user-attachments/assets/2a8f6681-c821-45e6-8aeb-d8c77c3583e7)

![WhatsApp Image 2024-09-16 at 9 43 05 PM](https://github.com/user-attachments/assets/c73e48f0-b2f7-465f-a6da-39ff5c86a31d)

![WhatsApp Image 2024-09-16 at 9 43 05 PM (1)](https://github.com/user-attachments/assets/2f6d4a55-53f6-4715-9f90-b3fb1eca3b76)


## setting the STA and creating the Base.sdc file

```bash
cd Desktop/work/tools/openlane_working_dir/openlane
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
```

Include newly added LEF files

```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

```bash
set ::env(SYNTH_SIZING) 1
```

running the synthesis 

```bash
run_synthesis
```

Newly created pre_sta.conf for STA analysis in openlane directory
Newly created my_base.sdc for STA analysis in openlane/designs/picorv32a/src directory

![Screenshot from 2024-09-16 17-46-22](https://github.com/user-attachments/assets/95c64f40-1eec-49ba-b1a8-669cca1ec7c6)
![Screenshot from 2024-09-16 17-48-41](https://github.com/user-attachments/assets/2179ab8e-461c-4c86-8243-7d2b723ecd1b)
![Screenshot from 2024-09-16 17-49-05](https://github.com/user-attachments/assets/ff8ab874-0201-49f1-b922-59eb33a8c27b)


Output of pre_sta.conf is equal to synthesis stage

```bash
sta pre_sta.conf
```

diong normal synthesis
![Screenshot from 2024-09-16 17-54-35](https://github.com/user-attachments/assets/f914baba-4576-44cf-b12b-3dc1e80e01fb)

## Clock Tree Synthesis
Step 1 
change the directory
```bash
cd ~/Desktop/work/tools/openlane_working_dir/openlane
```

Step 2

```bash
 docker
```

Step 3

```bash
./flow.tcl -interactive
```

Step 4

```bash
package require openlane 0.9
```

Step 5

```bash
prep -design picorv32a -tag 15-09_05-48 -overwrite
```

Step 6

```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

Step 7

```bash
set ::env(SYNTH_STRATEGY) "DELAY 3"
```
Step 8

```bash
set ::env(SYNTH_SIZING) 1
```
Step 9

```bash
run_synthesis
```
![Screenshot from 2024-09-16 18-02-37](https://github.com/user-attachments/assets/3567aeb2-15b7-4e9a-bd80-2bca3992dc7b)
![Screenshot from 2024-09-16 18-03-15](https://github.com/user-attachments/assets/9d843775-3001-417b-a554-a31df9d353d6)
![Screenshot from 2024-09-16 18-03-17](https://github.com/user-attachments/assets/d171018b-c046-4401-9851-721ac4c98a98)
![Screenshot from 2024-09-16 18-04-12](https://github.com/user-attachments/assets/8dd8e8c5-dc11-4725-87ca-9f31ee69d3e0)

Step 10

```bash
run_floorplan
```
![Screenshot from 2024-09-16 18-04-58](https://github.com/user-attachments/assets/e492f1de-66ea-4b80-b6e4-d0bb4ce1662a)

Running the cts
![Screenshot from 2024-09-16 18-05-58](https://github.com/user-attachments/assets/39ec2753-fbd7-4f48-8563-ecb6f56d3cfa)
![Screenshot from 2024-09-16 18-10-48](https://github.com/user-attachments/assets/4010c56a-2337-4b71-b091-23d82b16cc70)
Seeing the cts file
```bash
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-09_05-48/results/synthesis
```
![Screenshot from 2024-09-16 23-03-22](https://github.com/user-attachments/assets/6fa39185-124a-4b0d-9f1f-8a8d88a67560)

## After cts

running OpenROAD and performing the specified tasks

doing this in openlane terminal

Step 1 

```bash
openroad
```

Step 2

```bash
 read_lef /openLANE_flow/designs/picorv32a/runs/15-09_05-48/tmp/merged.lef

```

Step 3

```bash
read_def /openLANE_flow/designs/picorv32a/runs/15-09_05-48/results/cts/picorv32a.cts.def
```

Step 4

```bash
write_db pico_cts.db
```

Step 5

```bash
read_db pico_cts.db
```

Step 6

```bash
read_verilog /openLANE_flow/designs/picorv32a/runs/09-09_05-53/results/synthesis/picorv32a.synthesis_cts.v
```

Step 7

```bash
read_liberty $::env(LIB_SYNTH_COMPLETE)
```
Step 8

```bash
link_design picorv32a
```
Step 9

```bash
read_sdc /openLANE_flow/designs/picorv32a/src/base.sdc
```

Step 10

```bash
set_propagated_clock [all_clocks]
```

Step 11

```bash
exit
```
![Screenshot from 2024-09-16 18-13-38](https://github.com/user-attachments/assets/5017d48b-b94e-4d56-a5f5-dc58b50664ce)

![Screenshot from 2024-09-17 00-01-19](https://github.com/user-attachments/assets/0361eaaa-db3d-4f17-9275-24a38437889b)

![Screenshot from 2024-09-17 00-02-21](https://github.com/user-attachments/assets/bc8c1924-6682-4138-b032-0d41516570f6)
![Screenshot from 2024-09-17 00-03-23](https://github.com/user-attachments/assets/14e6766e-0ce1-4693-bc54-a867d61af025)

![Screenshot from 2024-09-17 00-04-28](https://github.com/user-attachments/assets/1ba46d79-935d-4983-b3df-7fc779ce218d)
![Screenshot from 2024-09-17 00-04-50](https://github.com/user-attachments/assets/63bd9d8d-be25-4b92-ad11-6080aff23981)
![Screenshot from 2024-09-17 00-21-36](https://github.com/user-attachments/assets/236236d4-9f8d-4d4e-a273-86f20d11c09e)
![Screenshot from 2024-09-17 00-23-03](https://github.com/user-attachments/assets/31738830-5af7-4999-bad8-8fe119ab1568)


## Sky130 Day 5 - Final steps for RTL2GDS using tritonRoute and openSTA
SKY_L4 - Routing topology algorithm and final files list post-route
### Power Distribution Network (PDN) Generation and Layout Exploration in OpenLANE

Change the Directory for invoking the openlane
Step 1 

```bash
cd ~/Desktop/work/tools/openlane_working_dir/openlane
```

Step 2

```bash
docker
```

Step 3

```bash
./flow.tcl -interactive
```

Step 4

```bash
package require openlane 0.9
```

Step 5

```bash
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

Step 6

```bash
set ::env(SYNTH_STRATEGY) "DELAY 3"
```

Step 7

```bash
set ::env(SYNTH_SIZING) 1
```
Step 8

```bash
run_synthesis
```
Step 9

```bash
init_floorplan
place_io
tap_decap_or
```

Step 10

```bash
run_placement
```

Step 11

```bash
run_cts
```
Step 12

```bash
gen_pdn
```
![Screenshot from 2024-09-16 18-02-37](https://github.com/user-attachments/assets/6c60832f-f08b-42b8-81d4-a224f31d227a)

![Screenshot from 2024-09-16 18-03-15](https://github.com/user-attachments/assets/2dc8b3ba-ad54-4da3-b9c9-a409d7ebb8f4)

![Screenshot from 2024-09-16 18-03-17](https://github.com/user-attachments/assets/ec8a48f1-607d-4e32-aed3-1f39bbf260ed)
![Screenshot from 2024-09-16 18-04-12](https://github.com/user-attachments/assets/ad616cf3-1ced-46fa-a75a-be9a318215d5)
![Screenshot from 2024-09-16 18-04-58](https://github.com/user-attachments/assets/254ff92b-9845-42ee-a82f-7543feb76dcf)

![Screenshot from 2024-09-16 18-05-58](https://github.com/user-attachments/assets/3340ef0d-88d3-43f0-9699-81983b785871)

![Screenshot from 2024-09-16 18-10-48](https://github.com/user-attachments/assets/7bfcf871-c6f7-4c7a-8368-5a5d7b9f9bf8)
![Screenshot from 2024-09-16 18-10-52](https://github.com/user-attachments/assets/709bea08-cb01-4f1e-a489-d2fdf56a0cd4)
![Screenshot from 2024-09-16 18-13-38](https://github.com/user-attachments/assets/f648acb7-ce66-4b15-860a-3219b9e809b9)

![Screenshot from 2024-09-16 18-45-00](https://github.com/user-attachments/assets/2b91911c-f5bb-47b2-90d6-7e3c06bf0991)

![Screenshot from 2024-09-16 18-47-03](https://github.com/user-attachments/assets/df368ad3-82cf-4eee-909f-0428167855d3)
![Screenshot from 2024-09-16 18-49-28](https://github.com/user-attachments/assets/8f521026-0749-46c1-8ce5-09b9d8d43f52)
![Screenshot from 2024-09-16 19-47-45](https://github.com/user-attachments/assets/3bd6706f-3a05-4abc-b7b7-84291226af20)
![Screenshot from 2024-09-16 20-43-09](https://github.com/user-attachments/assets/afcc2f1e-20b6-4b4a-aaaf-043664d7dee5)


