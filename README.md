==Introduction==
MOSTMetalCura is a customized version of [CuraEngine v.15.06](https://github.com/Ultimaker/CuraEngine/tree/15.06) (Latest version that supports Delta machine.) that converts a 3-D model (.STL) into G-code for the [MOST's open-source metal 3-D printer](http://www.appropedia.org/Open-source_metal_3-D_printer).

MOSTMetalCura is also called a slicer program because of the core operation of it, slicing. The CuraEngine is written in C++ and use the library called [Clipper](http://www.angusj.com/delphi/clipper.php) which is included in the source code. MOSTMetalCura is a console application without the GUI.

MOSTMetalCura was customized to support the [MOST's open-source metal 3-D printer](http://www.appropedia.org/Open-source_metal_3-D_printer). Configurations were added to the setting file, fdmprinter.json:
#machine_metal_printing (True/false; if false, then it operates as normal CuraEngine)
#machine_welder_on_gcode (G-code to turn on the welder)
#machine_welder_off_gcode (G-code to turn off the welder)
#machine_min_dist_welder_off (Minimum distance to travel that require the welder to be turned off)
#machine_layer_pause (True/false; pausing between layers)
#machine_layer_pause_gcode (G-code to specify how long to pause between layers)

MOSTMetalCura uses these and other settings to generate the proper G-code for the [MOST's open-source metal 3-D printer](http://www.appropedia.org/Open-source_metal_3-D_printer). For more details about settings, please see below.

==How to Install==
This is mainly for Linux OS machine.

#Clone or download a zip file of the repository from [MOSTMetalCura](https://github.com/mtu-most/MOSTMetalCura). If you download the zip file, unpack it to a wanted directory.
#Install Protobuf (See more details in README2 file.)
#Install libArcus (See more details in README2 file.)

Cmake compilation:
#Go to the MOSTMetalCura directory
#Execute the following commands
##mkdir build
##cd build
##cmake ..
##make

==Configuration==
You may want to adjust some settings to suit your printer in the configuration file, fdmprinter.json, which can be found in the MOSTMetalCura directory. The significant settings are:
*machine_start_gcode (Additional G-code to be inserted at the beginning of the G-code file.)
*machine_end_gcode (Additional G-code to be inserted at the end of the G-code file.)
*machine_metal_printing (True/false; if false, then it operates as normal CuraEngine.)
*machine_welder_on_gcode (G-code to turn on the welder.)
*machine_welder_off_gcode (G-code to turn off the welder.)
*machine_min_dist_welder_off (Minimum distance to travel that require the welder to be turned off.)
*machine_layer_pause (True/false; pausing between layers.)
*machine_layer_pause_gcode (G-code to specify how long to pause between layers.)
*machine_gcode_flavor (Which machine that generated G-code for?)
*layer_height (Printed layer height.)
*wall_line_count (Number of shell or perimeter lines.)
*wall_line_width (Width of a perimeter line.)
*infill_line_width (Width of inner fill line.)
*top_bottom_thickness (Thickness of top and bottom layers.)
*top_layers and bottom_layers (The amount of top and bottom layers respectively.)
*material_diameter (The filament diameter.)
*speed_print (Printing speed.)
*fill_sparse_thickness (Infill thickness.)

==How to Run==
MOSTMetalCura can be run from the terminal as command line.
#Go to the MOSTMetalCura directory.
#Edit "path/to/output/MOSTMetalCura.gcode" and "path/to/model/MOSTMetalCura.stl" in the following command and execute the new command.
#*./build/MOSTMetalCura -v -j fdmprinter.json -o "path/to/output/MOSTMetalCura.gcode" "path/to/model/MOSTMetalCura.stl"
#The generated G-code file will be in the directory you changed "path/to/output" to.
#You can load the G-code file into [Franklin](http://www.appropedia.org/Franklin) if you are using it as controlling software for your printer.
