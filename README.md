# KiCad_RFM95_Breakout_Board


## Project Information
This project is a PCB containing the RFM95 868MHz LoRa Chip and a low power STM32L053R8T6 microprocessor.

<img src="https://pngroyale.com/wp-content/uploads/2022/02/warning-sign-attention-warning-exclamation-mark-vector-graph.png" width="30">**CAREFUL:** Neither the schematic, nor the pcb layout has been validated! Please check yourself before using / producing this!

## Things to change for Rev 2.0:
- Make SWD connecter to 2.54mm so Jumpers can fit.
- Get USB to work or better use a USB to UART bridge for Serial communication via USB and programming

## Exporting for JLCPCB
### Generate Files
Open KiCad. In the PCB view, click on File -> Plot -> Generate Drill Files...\
Make sure the Output directory is "gerber/"\
Click on Generate Drill Files and Generate Map files, close the window and click on Plot.\
Then under File -> Fabrication Output -> Footprint Position, check to box to exclude all throughole components and generate the position file.\
In the schematics view, click on Tools -> Generate BOM, select the first option and generate.
### Convert files
JLCPCB uses another header than KiCad. To change the files accordingly, install [this tool](https://github.com/matthewlai/JLCKicadTools) by executing:
```bash
pip install git+https://github.com/matthewlai/JLCKicadTools
```
Move the position file from the geber folder to the main project folder, open a command prompt and execute:
```bash
jlc-kicad-tools .
```
Zip the gerber folder and now you have the new files ready for JLCPCB.

# HINT
The CPW signal trace of the RFM Chip to is set to 50+5% Ohms impedance for FR4 material and 1.6 mm board thickness. The distance between signal and GND top plane is set to 0.2 mm.
Use e.g. [ CPW impedance calulator](https://chemandy.com/calculators/coplanar-waveguide-with-ground-calculator.htm) for calulate the impedance.
