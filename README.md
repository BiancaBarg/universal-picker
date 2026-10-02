# Universal Picker

made by Bianca Bargan

A free beta picker for Maya and Blender. Named controls, clear Body / Face / Fingers views, and a separate picker remembered for each character in your scene.

## Download 1.18.1

| Application | Download | Verification |
| --- | --- | --- |
| Maya 2025 | [Maya ZIP](https://github.com/BiancaBarg/universal-picker/releases/download/v1.18.1/UniversalPicker-Maya-1.18.1.zip) | Verified in Maya 2025.3.2 on macOS, on human and quadruped rigs |
| Maya 2026 | [Same Maya ZIP](https://github.com/BiancaBarg/universal-picker/releases/download/v1.18.1/UniversalPicker-Maya-1.18.1.zip) | Beta compatibility build; full Maya runtime test pending |
| Maya 2027 | [Same Maya ZIP](https://github.com/BiancaBarg/universal-picker/releases/download/v1.18.1/UniversalPicker-Maya-1.18.1.zip) | Beta compatibility build; full Maya runtime test pending |
| Blender 5.2.2 LTS | [Blender ZIP](https://github.com/BiancaBarg/universal-picker/releases/download/v1.18.1/UniversalPicker-Blender-1.18.1.zip) | Verified on macOS with human and quadruped test armatures |

Maya 2026/2027 have separate Qt 6.5.3 / Qt 6.8.3 canvas checks. These do not replace testing inside those Maya versions.

## Maya: start in three steps

1. Unzip the Maya ZIP. Drag **install.py** into the Maya viewport. Choose **Replace** if updating.
2. Select your character and click **Capture view**.
3. Click the named buttons. Save your Maya scene to keep your picker.

One Maya installer is shared by 2025, 2026, and 2027.

## Blender: start in three steps

1. **Preferences → Get Extensions → menu → Install from Disk**. Choose the Blender ZIP; keep it zipped.
2. In the 3D View, press **N → Picker**. Select your character, then **Use selected rig → Open picker**.
3. Click the named buttons. Save your **.blend** file to keep your picker.

## Everyday controls

- **Capture view:** take a character reference picture.
- **Delete capture:** remove the picture and keep the buttons.
- **Add selected:** add several selected controls together.
- **Body / Face / Fingers:** focus on the controls you need.
- **Blue = left · Red = right · Yellow = center.** Shift adds; Ctrl toggles.

Maya also provides **Customize** for moving buttons and **How to use** for a short guide. **All controls** exposes extra controls in both applications.

This beta recognizes common controller names. Use **All controls** and **Add selected** for unusual rigs. Blender currently supports armature pose controllers. Full verification details are included in each ZIP.

[Latest release and checksums](https://github.com/BiancaBarg/universal-picker/releases/latest)
