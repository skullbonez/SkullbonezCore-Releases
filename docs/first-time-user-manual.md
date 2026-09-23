# SkullbonezCore
First-time user manual

Drive. Rewind. Build. Explore another future.

A guided introduction to your physics playground.

Public release edition - 23 September 2026

## Start here
Thank you for checking out SkullbonezCore's first public build. Download the Windows x64 ZIP from github.com/skullbonez/SkullbonezCore-Releases, extract the whole archive to a writable folder, and run Launch SkullbonezCore.cmd. Keep the data folder and DLLs beside the executable. Windows x64 and a compatible DirectX 12 GPU and driver are required; this build is unsigned.

### First, look and move
Start tutorial opens a camera lesson before you get into the car. Hold the right mouse button over the scene and move the mouse to look around. Keep right mouse held and press W, A, S or D to move. Complete both checklist items before continuing to the car.

### Find your way
The tutorial card shows your progress and offers Retry section, Skip step and Exit. The next editor button flashes yellow. Camera movement is slower during tutorial practice to make the scene easier to explore.

### Keep this guide nearby
This manual is included in the ZIP and linked from the public repository README. The public repository also accepts bug reports. Include your release version, reproduction steps and what you expected to happen.

## Your first crash
Click Tutorial in the top bar to start the crash course, or choose Start tutorial on first launch. Returning users can open Keys in Tools and choose Resume or Restart. The tutorial card follows your progress and offers Retry section, Skip step and Exit. The next editor button flashes yellow.

### Get in and drive
Double-click the car to attach the camera, then press T to drive. Esc detaches the camera. Hold W to accelerate, use A and D to steer, S to reverse and Space to brake. Drive into the blocks and watch the ragdolls fly.

### Watch it backwards
Press T to get out of the car. Move to the bottom edge to reveal the timeline. Drag its thumb left to watch your own crash run backwards. This views recorded history; it does not rewrite the live scene.

### Try again
If you miss the stack, click Retry section on the tutorial card to immediately restore the section's original level state. Click Continue when the tutorial offers the building chapter. It restores a clean, paused playground for editing.

## Make the stack yours
Press Esc to bring up the menu, then click Editor at the left edge to reveal its panel. In Objects, click Edit scene, then Select. Click the yellow top block. The chosen tool stays active until you choose another.

### Move, rotate and scale
Click Move [W] and drag an arrow for one axis, or a square plane handle for two axes. Keep the block close to the stack so the projectile can still hit it.

Click Rotate [E] and drag one of the rings. A small twist is enough. Click Scale [R] and drag the centre handle to resize uniformly. Axis handles resize representable shape axes; unavailable axes appear grey. Select [Q] returns to selection. These shortcuts apply when you are not holding right mouse to navigate.

### Undo and redo
Press Ctrl+Z or click Undo to restore the previous size, then press Ctrl+Y or click Redo to keep your change. Both keyboard shortcuts and buttons complete the tutorial steps. One completed drag is one history step. Escape during a drag cancels the edit and restores its starting transform without adding a history step.

### Set orientation and snapping
Space: World uses fixed world axes. Click it to use Space: Local and follow the selected object's orientation. Move snap, Angle snap and Scale snap toggle independently; the adjacent value button chooses the increment. Settings stay fixed while a drag is active.

## See a crash before it happens
Click Edit scene again to leave editing. Reveal Replay on the left, click Predict, then click the purple ball. Wait for its future path and Causes to appear. The live scene remains paused.

### Inspect a collision
In Causes, click the first Manifold row under the yellow block. The contact manifold shows the points where the objects will touch. Click Exit inspect at the top of the Causes pane to return to Scene mode. Click the purple ball again to select its future.

### Make another future
Click Modify velocity in Replay. Drag an arrow on the ball's velocity vector and release. Original stays available while Modified is calculated. Drag the timeline forwards and backwards to compare both paths.

### Choose and launch
Click Accept Original or Accept Modified. Either is a valid choice; acceptance does not launch the ball. Click Predict to turn it off, then click Play on the bottom transport. Watch the selected future play out against your edited stack.

## Build a new landscape
Click Continue to open the fresh landscape chapter. These edits begin paused. The left Editor panel provides Objects, Terrain and Material tabs.

### Shape the ground
Click Terrain. With Terrain brush enabled, hold left mouse on clear ground to raise a hill. Adjust Brush radius with its slider. Click Brush: Raise ground to change to Brush: Lower ground, then use left mouse to lower terrain. Right-drag moves the camera.

### Add water and colour
Use Water level or + 1 m to make a shoreline. Show water controls visibility. In Material, click the launcher block under the purple ball, then choose a colour. Choose Ground to colour the terrain. Rocket League grass is the turf surface; scene lighting is controlled separately.

### Add some chaos
Click Objects. Scroll to Tornado and click beside the stack to place it. Choose Bomb and place it on the other side. Leave the default delays for the tutorial. Scroll back to the top and click Edit scene to leave editing; click Play if paused. Wait for both effects to activate.

## Move around the viewport
The first tutorial lesson teaches looking and moving. These additional navigation controls help you explore afterwards. Start a gesture over the scene, clear of panels and text fields.

### Look and fly
Hold right mouse and move the mouse to look around. While holding it, W/S moves forwards/backwards, A/D strafes, Q moves down and E moves up along world Y. The wheel adjusts flight speed; Shift gives a temporary speed boost. Releasing right mouse restores the selected tool.

### Pan, orbit and zoom
Middle-drag pans in the camera plane. Alt-left-drag orbits the current focus; Alt-right-drag dollies towards or away from it. Alt-middle also pans. In an orthographic view, right-drag pans instead of rotating. The idle wheel changes zoom.

### Frame and choose a tool
Click Frame selected to fit the selected object. The optional idle viewport keys are Q Select, W Move, E Rotate, R Scale and F Frame selected. These mappings apply to editing and free inspection; vehicle, launcher and director modes keep their own controls.

### Leave inspection
Click Exit inspect on the causal pane, or press Escape. A popup dismisses first; an active transform cancels first. Exiting inspection returns camera ownership to Scene without launching the paused experiment.

## Save, recover and keep exploring
The tutorial uses bundled practice scenes that are protected from overwrite. To build your own saved level, click New scene in Editor > Objects, make your edits, then click Save scene. This updates that authored level through its normal save and backup handling. F2 exports a separate scene shot; it does not save the active level. Tutorial progress is separate from scene files.

### Resume or restart
Resume reconstructs the current chapter's starting setup. It cannot recreate a previous session's temporary recording or calculated futures. Restart begins with looking and moving, before the car. Retry section restores the current chapter. Skip step marks a lesson as skipped; it is not the same as completing it.

### Load a level safely
The level-authoring guide explains the accepted scene format and the shipped native validator. See docs/LLM-Level-Authoring-Prompt.md for the long-form prompt, examples, validation commands and the generate-check-fix loop. A successful format check does not prove that a structure is stable or a track is drivable.

### Lighting and materials
Split Future lighting is the default across scenes. F7 switches to legacy lighting for comparison. Rocket League grass is a terrain material with no specular highlight. The authored Split Future scene retains its separate ground material.

### More help
Open Keys in Tools for controls outside the tutorial. Use visible controls whenever possible. For a stuck step, Retry section gives a known starting point without overwriting your saved scenes.

## Editor entry and status
Click Edit scene to inspect and select existing objects. Choosing an object to place in Objects or Build automatically enters Edit mode with that object ready to place. Terrain align, Modify velocity and Angular velocity sit near the top of Objects.

The right side of the top bar shows Objects on the first line, then Scene and Frame on the second. Solver Lab in Tools > Scene can open separately supplied comparisons. The compact public ZIP omits the large built-in comparison bundles.

## Replay controls and the final lesson
Predict is the bold first control in Replay. Modify velocity is directly below it. Select a predicted object to work with its velocity, then compare Original and Modified before accepting one.

### Recording controls
High detail prediction sits above Save recording. Load recording follows Save recording; Branch from here [Enter] is the final control beneath Load recording. Branching resumes simulation from the selected recorded point. Save a recording if you want to keep a separate copy before exploring a different branch.

### Explore the Solar System
The final tutorial chapter opens Tools > Scene. Search for the Solar System, load it, increase the prediction horizon to at least 40 seconds, then press Play. Finishing the tutorial leaves the Solar System running. The earlier practice scenes use a 20-second playback limit.

### Water appearance
Demo water is the default appearance. Reflection perturbation is disabled in this release. Terrain editing and water-level controls still let you build a shoreline.
