# Easy Clothes Setup Addon for Blender

## Overview

The **Easy Clothes Setup Addon** is a Blender addon designed to streamline the process of setting up clothes with armatures. It provides an easy-to-use interface for combining clothes with a target armature and transferring weights while maintaining the original bone structure. This tool is ideal for 3D artists who need a quick solution for setting up garments with rigs.

### Key Features

- **Combine Clothes with Armatures**: Easily parent selected meshes to a target armature.
- **Transfer Extra Bones**: Automatically transfer extra bones from the original armature to the new one, maintaining the original skeleton structure.
- **Debug Mode**: Visual feedback to ensure meshes and armatures are correctly set up.
- **Instruction Panel**: A quick guide to help new users understand the workflow.

## Installation

Follow these steps to install the Easy Clothes Setup Addon in Blender:

### 1. Download the Addon Script

- Copy the addon code provided and save it as a Python file named `easy_clothes_setup.py`.

### 2. Launch Blender

- Open Blender on your computer.

### 3. Open Preferences

- Go to **Edit** > **Preferences**.

### 4. Navigate to the Add-ons Section

- In the Preferences window, click on the **Add-ons** tab on the left sidebar.

### 5. Install the Addon

- Click the **Install...** button at the top of the Preferences window.
- Navigate to the location where you saved `easy_clothes_setup.py`.
- Select the file and click **Install Add-on**.

### 6. Enable the Addon

- After installation, the addon will appear in the list of available add-ons.
- Check the box next to **Easy Clothes Setup Addon** to enable it.

### 7. Save Preferences (Optional)

- To keep the addon enabled for future Blender sessions, click **Save Preferences** at the bottom of the Preferences window.

## Usage

### Accessing the Addon

1. **Select Your Mesh Objects**

   - In the **3D Viewport**, select the mesh objects you want to combine with an armature.

2. **Open the Easy Clothes Setup Panel**

   - Go to the **Sidebar** (`N` key) in the **3D Viewport**.
   - Navigate to the **Easy Clothes** tab.

3. **Set the Target Armature**

   - In the **Easy Clothes Setup** panel, use the dropdown to select your target armature.

4. **Combine the Clothes**

   - Click on the **Combine Clothes** button to parent the selected meshes to the target armature.

5. **Debug the Setup**

   - Open the **Debug** foldout to check the setup status and ensure everything is configured correctly.

### Debug Mode

- **Meshes Selected**: Shows whether meshes are selected.
- **Armature Reference**: Indicates if the target armature is set.
- **Meshes Under Armature**: Checks if meshes are parented to the correct armature.
- **Extra Bones**: Detects any extra bones that need to be transferred.

## Parameter Explanation

- **Target Armature** (`wm.target_armature`): The armature that selected clothes will be combined with.  
  - Make sure to select the correct armature for the setup.

- **Transfer Extra Bones** (`wm.transfer_extra_bones`): Boolean option to enable or disable the transfer of extra bones from the original armature to the target armature.  
  - Enable this if your target armature needs additional bones from the original rig.

## Example Workflow

### Scenario

You have multiple clothing meshes that were previously rigged to different armatures. You want to combine them all under a new target armature without losing the additional bone data.

### Steps

1. **Set Parameters**:

   - **Target Armature**: Select the armature that will serve as the main rig.
   - **Transfer Extra Bones**: Enable this option to ensure all relevant bones are transferred.

2. **Run the Combine Operation**:

   - Select all clothing meshes and click **Combine Clothes**.

3. **Result**:

   - All selected meshes are now parented to the new target armature with extra bones transferred, if applicable.

## Troubleshooting

- **No Meshes Selected**:  
  - **Issue**: Operator reports "No meshes selected."
  - **Solution**: Select at least one mesh object before running the operation.

- **No Target Armature Assigned**:  
  - **Issue**: Operator reports "No target armature assigned."
  - **Solution**: Use the **Target Armature** dropdown in the panel to assign an armature.

- **Original Armature Not Deleted**:  
  - **Issue**: The original armature was not removed.
  - **Solution**: Ensure the option for transferring extra bones is set correctly, or manually delete the original armature.

## Limitations

- **Armature Compatibility**:  
  This addon is designed for armatures with similar structures. Using significantly different armatures may lead to unexpected results.

- **No Built-in Undo**:  
  The operator doesn’t have an internal undo feature. Use Blender’s undo function (`Ctrl + Z`) if needed.

## Best Practices

- **Backup Your Work**:  
  Always save your project before running operations that modify data extensively.

- **Test on a Duplicate**:  
  Consider duplicating your mesh and armature (`Shift + D`) and testing the operation on the copy.

- **Apply Transforms**:  
  Make sure to apply all transforms (`Ctrl + A > All Transforms`) before combining clothes.
