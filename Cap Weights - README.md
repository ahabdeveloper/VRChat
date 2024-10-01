# Cap Weights Addon for Blender

## Overview

The **Cap Weights Addon** is a Blender addon designed to help users manipulate vertex group weights efficiently during weight painting. This tool allows you to adjust vertex weights based on specified thresholds and multipliers, providing greater control over weight distribution in your 3D models.

### Key Features

- **Process Active Vertex Group**: Modify weights only in the currently active vertex group.
- **Adjustable Parameters**: Set custom thresholds and multipliers to fine-tune weight adjustments.
- **User-Friendly Interface**: Accessible through the Weight Paint context menu with an intuitive popup dialog for parameter input.

## Installation

Follow these steps to install the Cap Weights Addon in Blender:

### 1. Download the Addon Script

- Copy the addon code provided and save it as a Python file named `cap_weights_addon.py`.

### 2. Launch Blender

- Open Blender on your computer.

### 3. Open Preferences

- Go to **Edit** > **Preferences** (or **File** > **User Preferences** in older versions of Blender).

### 4. Navigate to the Add-ons Section

- In the Preferences window, click on the **Add-ons** tab on the left sidebar.

### 5. Install the Addon

- Click the **Install...** button at the top of the Preferences window.
- Navigate to the location where you saved `cap_weights_addon.py`.
- Select the file and click **Install Add-on**.

### 6. Enable the Addon

- After installation, the addon will appear in the list of available add-ons.
- Check the box next to **Cap Weights Addon** to enable it.

### 7. Save Preferences (Optional)

- To keep the addon enabled for future Blender sessions, click **Save Preferences** at the bottom of the Preferences window.

## Usage

### Accessing the Addon

1. **Select Your Mesh Object**

   - In the **3D Viewport**, select the mesh object you want to modify.

2. **Switch to Weight Paint Mode**

   - Press `Ctrl + Tab` and select **Weight Paint**, or use the mode selector at the top-left corner of the 3D Viewport.

3. **Ensure an Active Vertex Group is Selected**

   - In the **Object Data Properties** panel (represented by a green triangle icon), make sure you have a vertex group selected.
   - The active vertex group is the one highlighted in the list.

### Using the Cap Weights Operator

1. **Open the Context Menu**

   - Right-click anywhere in the **3D Viewport** while in **Weight Paint** mode to open the context menu.

2. **Select the Cap Weights Operator**

   - From the context menu, click on **Cap Weights - VG**.

3. **Adjust Parameters in the Popup Dialog**

   - A popup dialog will appear with the following adjustable parameters:

     - **Limit Old Weight**: Threshold above which vertex weights will be modified.
     - **Limit New Value**: Minimum value that modified weights can be set to.
     - **Multiplier Value**: Factor by which weights exceeding the limit are multiplied.

   - **Default Values**:

     - **Limit Old Weight**: `0.35`
     - **Limit New Value**: `0.35`
     - **Multiplier Value**: `0.7`

   - Adjust these values as needed for your project.

4. **Execute the Operation**

   - Click the **OK** button to run the operator.
   - The addon will process the selected vertex group or all vertex groups based on your settings and adjust the weights based on your parameters.

## Parameter Explanation

- **Limit Old Weight** (`limit_old_weight`): Vertices with weights above this value will be modified.  
  - Example: If set to `0.35`, only vertices with weights greater than `0.35` are affected.

- **Limit New Value** (`limit_new_value`): Ensures that modified weights do not fall below this value.  
  - Example: If a calculated weight is `0.3` but the limit is `0.35`, the weight is set to `0.35`.

- **Multiplier Value** (`multiplier_value`): The factor by which eligible weights are multiplied.  
  - Example: A weight of `0.5` multiplied by `0.7` becomes `0.35`.

## Example Workflow

### Scenario

You have a mesh where certain vertex weights are too high, causing deformation issues during animation. You want to reduce these weights but ensure they don't drop below a minimum value to maintain smooth transitions.

### Steps

1. **Set Parameters**:

   - **Limit Old Weight**: `0.6` (weights above this will be adjusted).
   - **Limit New Value**: `0.4` (weights won’t go below this value).
   - **Multiplier Value**: `0.8` (weights are multiplied by this factor).

2. **Run the Operator**:

   - Follow the usage instructions to execute the operator with these parameters.

3. **Result**:

   - Weights above `0.6` are reduced by 20% but not below `0.4`.

## Troubleshooting

- **No Active Vertex Group Selected**:  
  - **Issue**: Operator reports "No active vertex group selected."
  - **Solution**: In **Object Data Properties**, select a vertex group to make it active.

- **Active Object Is Not a Mesh**:  
  - **Issue**: Operator reports "Active object is not a mesh."
  - **Solution**: Ensure you've selected a mesh object before running the operator.

- **Weights Not Changing as Expected**:  
  - **Issue**: Weights remain the same after running the operator.
  - **Solution**: Verify that your parameters are correctly set and that the vertex weights exceed the **Limit Old Weight**.

## Limitations

- **No Built-in Undo**:  
  The operator doesn’t have an internal undo feature. Use Blender’s undo function (`Ctrl + Z`) if needed.

- **Performance on Large Meshes**:  
  Processing very large meshes may take some time. Be patient while the operator runs.

## Best Practices

- **Backup Your Work**:  
  Always save your project before running operations that modify data extensively.

- **Test on a Duplicate**:  
  Consider duplicating your mesh (`Shift + D`) and testing the operator on the copy.

- **Adjust Parameters Gradually**:  
  Start with small adjustments to understand how the parameters affect your mesh.
