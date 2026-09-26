# SkullbonezCore
First-time user manual

Explore. Build a scene. Test what happens.

Windows release 2026.09.26

## Your first session
<!-- section: GET STARTED -->

This guide helps you explore, build and test your own SkullbonezCore scenes.

### 1. Extract, then launch
Download the Windows ZIP from the [public release page](https://github.com/skullbonez/SkullbonezCore-Releases/releases). Extract the entire archive to a writable folder and run **Launch SkullbonezCore.cmd**. Keep the executable, DLLs and **SkullbonezData** together. You need 64-bit Windows and a DirectX 12-compatible GPU and driver. This build is unsigned; no development tools are needed.

### 2. Learn to look and move
Choose **Start tutorial** on first launch, or click **Tutorial** in the top bar. Use the tutorial title-bar minus button to collapse it on a small screen; plus restores it. The first lesson teaches the camera. Hold **right mouse** over the scene and move the mouse to look around. Keep it held and use **W/A/S/D** to move. Release right mouse to use panels and tools again.

### 3. Find the controls
Press **Esc** to open the menu, then open **Editor** at the left edge. **Tools > Scene** loads levels; **Tools > Keys** shows controls and tutorial Resume/Restart. Hover for help and scroll inside panels. The top-right header shows Objects, then Scene/Frame on the next line.

### Start with these controls
| Control | What it does |
| --- | --- |
| Right mouse + move mouse | Look around the viewport. In an orthographic view, pan instead. |
| Right mouse + W/A/S/D | Move forward, left, backward and right. Q/E moves down/up. |
| Shift / wheel while looking | Temporary speed boost / adjust flight speed. |
| Middle-drag / idle wheel | Pan the camera / zoom. |
| Double-click an object | Attach the camera. For a car, press T to enter Drive. |
| W/A/S/D / Space in Drive | Accelerate, steer, reverse / brake. Esc detaches. |
| Top-bar Edit / Playback | Red means editing; green means playback. Click to switch. Edit scene mirrors it. |
| 0 (zero) | Show or hide the UI. |

> **Good to know**
> The tutorial covers driving, rewinding, editing, terrain and the Solar System. **Retry section** restores the current chapter; **Skip step** moves past a lesson. Practice scenes are protected: use **New scene** to make a level you can save.

## Build your first scene
<!-- section: CREATE A SCENE -->

Example: a box and a ball on flat terrain. The Objects list also includes a narrow, marked **Domino** and a **Red arch** with an open doorway.

### 1. Open the Editor
Open **Editor > Controls**. Save existing work before starting a new level.

### 2. Create a new scene
Click **New scene** for a blank editable scene. Its name appears in **Tools > Scene**.

### 3. Find the placement controls
Open **Objects** and choose a type from the scrollable object list to enter placement automatically. **Edit scene** controls editing; **Select [Q]** returns to selecting existing objects.

### 4. Place a box
Choose **Box**. Turn **Static object** on for a fixed obstacle, or off for a body that can fall. Move onto terrain until the preview appears, then click and release left mouse to place it.

### 5. Add a ball
Choose **Ball** and turn **Static object** off. Move the preview near the box. Before placing, use the wheel to raise it above the terrain, then click and release. Page 3 explains sizing and rotation.

### 6. Save the scene
Click **Save scene** in **Editor > Controls**. This writes the authored level under **SkullbonezData/scenes/**. Check the save feedback before changing scenes or closing the app. **F2** makes a separate scene shot; it does not save the active level.

### 7. Run your experiment
Click **Play**, including from Edit mode. Press **6** to restore your edited starting arrangement and clear the timeline. Unsaved edits survive reset; reset does not save the scene.

### 8. Reopen and try again
Find saved levels in **Tools > Scene**. Edit, save and run again. Scenes and replay recordings are separate saves (page 4).

> **Good to know**
> Creating a scene does not replace saving it. Use **Save scene** for your authored level. Tutorial practice scenes cannot be overwritten; create your own level to keep changes.

### Minecraft mouse controls
Enable **Minecraft mode** in Controls. Click the viewport to capture the mouse; **left-click places**, **right-click removes**, **Esc releases**. **Wheel zooms**, **Ctrl-wheel rotates**, **Shift-wheel adjusts height**. **1 Move / 2 Rotate / 3 Scale** release the mouse for editing; **4 turns 90 degrees / 5 snaps to ground / 6 resets**. Keys 4/5 affect the preview or selected blocks. Choose an object in Objects to resume placing.

### Ragdoll colliders
Open **Physics > Visualisation > Ragdoll colliders**: **Off**, **Selected Ragdolls**, or **All Ragdolls**. Select any part to see its whole ragdoll. New heads use sphere colliders; older saved box heads retain their physics.

## Place, select, transform
<!-- section: EDITOR WORKFLOW -->

The pointer acts on the viewport. A click over a panel operates that panel instead.

| Mode | Use it for |
| --- | --- |
| Choose a type in the object list | Preview and insert a new object. Placement enters Edit mode automatically. |
| Select [Q] | Select an existing object, then choose Move, Rotate or Scale. A gizmo is the visible set of transform handles. |

### Placing objects
| Gesture or control | Result |
| --- | --- |
| Left click and release | Place the current preview. Placement commits on release. |
| Hold left mouse + drag | Resize before placing. Boxes use drag for footprint dimensions and wheel for height during the drag; round objects scale uniformly. |
| Wheel before clicking | Raise/lower the preview; use Shift-wheel in Minecraft, where plain wheel zooms. |
| Ctrl + wheel | Rotate the preview around the vertical axis in 15-degree steps. |
| Static object / Terrain align | Choose fixed or dynamic physics / align placement to the terrain slope. |

### Editing existing objects
Click **Select [Q]**, then an object. Keep **Modify velocity** off for shape edits. Release right mouse before using tool shortcuts.

| Tool or gesture | Result |
| --- | --- |
| Move [W] | Drag an arrow along one axis, or a square handle in a plane. |
| Rotate [E] | Drag a ring to rotate around its axis. |
| Scale [R] | Drag the centre for uniform size, or an axis for supported shape dimensions. |
| Space: World / Local | Choose fixed world axes or axes aligned to the object. |
| Move / Angle / Scale snap | Toggle snapping and choose each increment with its value control. |
| Esc during a drag | Cancel the edit and restore the starting transform. |
| Ctrl-click / Ctrl+C / Ctrl+V | Add to a selection / copy / paste standalone objects together, keeping their arrangement. |
| Make static / Make physical | Convert selected blocks in place, including blocks in an older saved level. Save afterwards. |
| Delete / Ctrl+Z / Ctrl+Y | Delete / undo / redo. Ctrl+Shift+Z also redoes. |

**Camera:** right mouse + W/A/S/D flies; middle-drag pans. **Frame selected [F]** fits the selection in view.

> **Good to know**
> Save your starting scene. Use undo before leaving Edit mode, which clears edit history. A grey axis means that change is unavailable.

## Physics, prediction & replay
<!-- section: TRY AN EXPERIMENT -->

Start simple: save a scene, run it, inspect what happens, then reload your saved setup.

### Control the simulation
Use **Play/Pause** on the bottom transport; Play can leave Edit mode for you. The scrubber is grey and cannot be dragged until there is recorded or predicted time to inspect. Play creates a new future. Static bodies stay fixed; physical bodies can move.

### 1. Predict and inspect
Open **Replay** and click the bold **Predict** control, then click a body in the viewport. Wait for its future path and **Causes**. Click a cause to inspect a collision; **Exit inspect** or **Esc** leaves inspection without launching the paused experiment.

### 2. Compare a different future
**Modify velocity** sits directly below Predict. With a predicted object selected, enable it, drag a velocity arrow and release. Compare **Original** and **Modified** by scrubbing the timeline. Choose **Accept Original** or **Accept Modified**, turn Predict off, then press **Play** to launch it.

### 3. Rewind, edit or branch
Drag the timeline thumb to inspect recorded history. Switch to **Edit** to return to the starting arrangement. If you change nothing, **Playback** returns to the retained time. The first edit discards that future, even if undone; Play then runs from the start. **Branch from here [Enter]** in Replay instead resumes from the selected recorded point.

### Understand the different saves
| Action | What you keep |
| --- | --- |
| Editor > Controls > Save scene | The editable authored level under SkullbonezData/scenes/. |
| F2 | A separate numbered scene shot; it does not save the active level. |
| F3 | A viewport screenshot. |
| Replay > Save / Load recording | Recorded simulation data, separate from the editable scene. High detail prediction is just above Save recording. |

> **Good to know**
> **Reset [6]** restores the edited starting arrangement and clears the timeline. Unsaved editor changes survive reset. **Reset Defaults** reloads authored defaults; save before using it or changing scenes.

### Director camera
In Edit mode, open **Camera** beside Replay. Move with right mouse and W/A/S/D; release right mouse and **Capture view** at two or more positions. Choose **Curve**, easing and **Faster / Slower**, then **Play path**. **Space** pauses/resumes; **B** grabs the view. **Save path / Load path** use a separate `.shot.json` file.


### Explore further
For a space experiment, load **solar_system.scene.json**, set **Prediction horizon** to **40s**, select **Earth**, **Predict**, then **Play**.

**Solver Lab** requires separately supplied comparisons; the portable ZIP omits them. Space plays/pauses; left/right arrows step.

## Keyboard & mouse
<!-- section: QUICK REFERENCE -->

Finish typing or close popups before using shortcuts. Release right mouse for tools. Vehicle and launcher controls depend on their modes.

| Key / gesture | Action and context |
| --- | --- |
| Right mouse + move mouse | Viewport camera look; pan in an orthographic view. |
| Right mouse + W/A/S/D; Q/E | Fly forward/left/back/right; down/up. |
| Shift / wheel while looking | Temporary faster travel / adjust flight speed. |
| Middle-drag / idle wheel | Pan / zoom. |
| Alt-left / Alt-right / Alt-middle drag | Orbit / dolly / pan around the current focus. |
| Q / W / E / R | Select / Move / Rotate / Scale in editing and free inspection. |
| F | Frame the selection in editing and free inspection. |
| Backtick (`) | Enter or leave Edit mode (US keyboard key below Esc). |
| Double-click / Esc | Attach to an object / detach. Esc dismisses or cancels an active interaction first. |
| T | Enter or leave Drive when attached to a car. |
| W/A/S/D / Space in Drive | Accelerate, steer, reverse / brake. |
| Ctrl+C / Ctrl+V | Copy / paste the selected standalone objects, including a multiple selection. |
| Ctrl+Z / Ctrl+Y or Ctrl+Shift+Z | Undo / redo an editor edit. |
| Delete / Esc during a transform | Delete the editable selection / cancel the drag. |
| Ctrl + wheel in placement | Rotate the preview by 15 degrees per wheel step. |
| P | Toggle paused prediction inspection. Use visible Play to run afterwards. |
| F1 / Enter when attached | Cycle attached-camera submode / toggle camera pin. |
| Enter in replay | Branch from the selected recorded point when available. |
| F2 / F3 | Save a separate scene shot / screenshot. |
| 0 / F7 | Show/hide UI / switch Split Future and legacy lighting. |
| N / M | Toggle launcher / cycle its fire mode while active. |
| Space / left-right in Solver Lab | Play/pause / step backward-forward. |
| V / C / G / O | Collision visuals / physics overlays / broadphase bounds / terrain contact probe. |
| 1 / 2 / 3 in Minecraft | Move / Rotate / Scale; replaces the old box-size presets. |
| 4 / 5 in Minecraft; 6 / Backspace | Turn 90 degrees / snap to ground; reset scene and clear timeline. |

**Q/W/E/R** still select tools in Minecraft after **Esc** releases mouse-look; captured **WASD** moves the camera. More controls: **Tools > Keys** and hover help.

## When something feels stuck
<!-- section: HELP & NEXT STEPS -->

Most first-session surprises come from an active mode, a paused scene, or a pointer over a panel.

| What you see | What to check |
| --- | --- |
| Objects will not move | Turn Predict off and press Play. Check the body is physical rather than static. |
| A large scene runs slowly | Options has independent Min-spec graphics and Min-spec physics checkboxes. Both are remembered. Graphics disables anti-aliasing and costly effects; fewer physics iterations can make complex stacks less stable. |
| Clicks keep adding objects | Choose Select [Q] before selecting an existing object. |
| The cursor disappears | Release right mouse. A placement preview can replace the normal cursor over the world. |
| No placement preview | Choose an object type and move over terrain inside the viewport, clear of panels. |
| Shortcuts do nothing | Finish editing the text field or close the popup. Check the mode and release right mouse for tool shortcuts. |
| Controls are missing | Scroll inside panels or open their docks. Collapse the tutorial with its minus button. Press 0 if the UI is hidden. |
| My scene is missing after restart | New scene alone does not save it. Use Editor > Controls > Save scene and check the save feedback. |
| Files do not save or assets are missing | Extract the whole ZIP to a writable folder and use Launch SkullbonezCore.cmd. Do not run from inside the ZIP. |
| A tutorial step is stuck | Use Retry section for a fresh chapter setup. Resume restores a chapter, not a previous session's temporary recording. |

### Terrain and water
In Edit mode, open **Terrain**, enable **Terrain brush**, then hold **left mouse** to paint. Use **Brush: Raise ground / Lower ground** to choose the direction and **Brush radius** to set its size. Right-drag moves the camera. Use **Water level** and **Show water** to make a shoreline. Save your authored scene afterwards.

### A useful first practice session
Create a new scene, place one static box and one dynamic ball, save, leave editing and watch. Reload, move the ball higher, save again and use **Predict** to explore the result. Or follow **Tutorial** from its camera lesson through the Solar System finale.

### About this guide
A practical guide to **SkullbonezCore 2026.09.26**, covering the editor, camera navigation, scene saving, Replay and tutorial controls a new user needs first.

[Downloads and feedback](https://github.com/skullbonez/SkullbonezCore-Releases) - include your build version, what you did and what happened when reporting a problem. The online **LLM Level-Authoring Guide** is linked from the repository README.
