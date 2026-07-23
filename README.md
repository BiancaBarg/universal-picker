# Universal Picker for Maya

Universal Picker builds a clean, clickable animation picker from the rig
controllers you select. It does not require a rig-specific template, naming
standard, or setup node.

Designed for Autodesk Maya 2022–2026 on Windows, macOS, and Linux. The UI
supports both PySide2/Qt 5 and PySide6/Qt 6.

> **Beta version:** Universal Picker is free and still being improved. Please share
> your Maya version, operating system, rig type, screenshots, and any misplaced or
> missed controllers so I can make it work better with more rigs.

## Install

1. Download and unzip `UniversalPicker-1.13.0.zip`.
2. Keep `install.py`, `UniversalPicker.mod`, and the `UniversalPicker` folder
   together.
3. Start Maya.
4. Drag `install.py` from Explorer/Finder into a Maya viewport.
5. Click **Open Picker**. A cyan **UP** picture button is added to the current
   Maya shelf.

The installer places the module in Maya's user modules folder. It does not
modify the Maya application.

Universal Picker was made by Bianca Bargan.

## Build a picker

1. Choose the **Human** or **Quadrupeds** tab.
2. For a human rig, capture **Body** and **Facial**, adding the matching
   controllers to each view.
3. For a quadruped rig, capture **Body Left**, orbit to capture **Body Right**,
   and then capture **Facial**, adding the matching controllers to each view.
4. Turn on **Edit Layout** to drag the screenshot into exact alignment, or to
   move, rename, and delete controller shapes.
5. Click **Save to Scene**, then save the Maya scene.

Use **Save for Rig** after selecting one controller from the rig to keep a
reusable picker preset in your Maya user folder. In another scene, select one
controller from the same referenced rig and click **Load for Rig**. The rig
source-file identity is used, so changing its namespace does not break the
preset.

**Delete Scene Save** removes only the picker embedded in the current Maya
scene. **Delete Rig Save** permanently removes only the reusable rig preset.
**Reset Picker** clears the open picker without deleting either saved copy.
Opening a new Maya scene also resets the open picker automatically.

Each rig tab has independent **Show IK** and **Show FK** buttons. Names with
clear IK/FK tokens are classified automatically. For any other naming system,
select the controls in Maya and use **Set IK**, **Set FK**, or **Set Other**.
In Edit Layout, the same classification is available by right-clicking an
individual controller.

The picker automatically:

- separates Human and Quadrupeds into clear tabs;
- keeps independent Human Body and Facial views;
- keeps independent Quadruped Body Left, Body Right, and Facial views;
- detects the camera-nearest quadruped leg set independently in every side
  screenshot, so a blue-side view keeps blue legs and a red-side view keeps red
  legs regardless of the panel's Left/Right name;
- recognizes the wide eye-aim rectangle with its left/right oval controls,
  scales the cluster into a compact diagram, and docks it to the right of Human
  or Quadruped Facial screenshots;
- detects tongue and teeth controls from the same rig and preserves their curve
  arrangement in a compact group directly below the docked eye-aim diagram;
- saves each screenshot's Maya camera projection so controllers can be selected
  and added after the images are captured;
- clears the selection highlight and temporarily hides controller curves only
  while taking the clean screenshot;
- projects every control pivot into the matching screenshot coordinates;
- ignores selected mesh geometry, joints, and other non-controller objects;
- embeds the rig image directly in the picker and scene data;
- projects the selected NURBS controller curves themselves over the rig image,
  sampling the evaluated curves to preserve their real smooth shape, position,
  and viewport color;
- reads Maya viewport override colors;
- keeps full DAG paths and Maya UUIDs for referenced/namespaced rigs;
- updates Maya selection when buttons are clicked.

Controls outside the current camera view are placed in a compact tray below the
image, so no selected controller is lost. Use the **Rig Image** toggle to compare
the image-backed picker with the control layout alone. **Remove Screenshot**
deletes only that panel's image and keeps its controller shapes.

Normal click replaces the selection, Shift-click toggles a control, and
Ctrl-click removes a control. Right-click a button to select, add, set a key,
or frame it in the viewport.

Drag a box across picker controllers to select several at once. Shift-drag
toggles the boxed controls, Ctrl-drag removes them, Ctrl+Shift-drag adds them,
and Alt-drag pans the picker without selecting.

## Scene and JSON storage

**Save to Scene** stores the picker JSON and compressed viewport image on a Maya
`network` node. The rig is not modified. Save the `.ma` or `.mb` scene afterward
to persist it.

Use **Export JSON** to share or back up a layout. If controls are in a different
namespace when it is imported, Universal Picker first tries the Maya UUID and
then an unambiguous controller name.

## Important rig-agnostic behavior

Each saved viewport projection is camera-accurate: buttons begin where their
controls appear in its Body or Face image. If several controls overlap,
Universal Picker separates their buttons slightly to keep every control
clickable.

The tool selects controls; it does not edit constraints, animation, the rig
hierarchy, or referenced rig files.

## Optional Maya command plug-in

The shelf button opens the tool directly. Pipeline users can instead load the
included Python command plug-in:

```python
from maya import cmds

cmds.loadPlugin("universalPicker.py", quiet=True)
cmds.universalPicker()
```

## Add or repair the UP shelf button

After Universal Picker is installed, switch Maya's command line or Script
Editor to **Python** and run:

```python
import universal_picker; universal_picker.install_shelf_button(); universal_picker.show()
```

This creates or updates the button on the currently selected shelf, assigns the
included cyan UP icon, and opens the picker.

## Development verification

Run the pure-Python checks outside Maya:

```bash
python3 -m unittest discover -s tests -v
```

The test suite covers Human and Quadruped pages, IK/FK classification, saved
camera projection, embedded-image persistence, off-camera controls,
deterministic placement, collision prevention, schema validation, and JSON
round trips.
