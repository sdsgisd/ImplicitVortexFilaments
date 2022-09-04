How to save and load simulation results?

[Only curves]
You can save curve data using "dopio_curve" node.
The saved data of curves can be loaded by "dopio_load_curve". 

To use the curve data for simulation in "dopnet_filaments" node, edit "sopgeo_curve" node in "dopnet_filaments" as follows.
- change SOP Path from "../../Curve" to "../../LoadedCurve" 
- change the parameter of "Time" from "Use Default" to "Set Always".
Then the simulator can run without any solvers for curves.

This technique can be used for many purposes. For example, you can first run simulation only for curves, and then run simulation only for particles or smoke using the saved curve data.

[All the data]
Use "file_save_and_load" node in "dopnet_filaments" node both for saving and loading simulation results. 
Read Files, Write Files, Automatic (read if there is a saved file, otherwise write) can be chosen.