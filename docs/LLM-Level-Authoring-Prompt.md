# Create a Skullbonez level with an LLM

Authoring format: **skullbonez.scene.json, version 9**. This guide and its
`level-authoring/` examples travel with the tester build. Windows PowerShell 5.1
or newer and the installed Skullbonez executable/data are the only validator
prerequisites. A DX12-capable machine that can run the game is required. No Python,
Visual Studio or developer checkout is needed.

Copy everything below into a fresh LLM conversation. Attach the two example JSON
files and `level-authoring/asset-catalog.json` if the assistant cannot read local
files. The examples are complete files, not fragments. The minimal example creates
one block; the worked example launches a red box into three blue blocks.

---

You are helping me author a playable Skullbonez level. My desired level is:

**[PASTE YOUR LEVEL DESCRIPTION HERE]**

My installed app folder is **[e.g. C:\Games\Skullbonez]** and my output folder is
**[e.g. C:\Users\Me\Documents\My Levels]**.

Use this guide as the supported authoring contract. Translate my description into
objects, materials, initial conditions and terrain. Ask focused questions only
when ambiguity changes the intended result. State assumptions, and identify
features you cannot express. Do not invent object types, asset names, JSON keys,
Lua scripts or arbitrary event logic. Use small bounded scenes initially.

Write a NEW UTF-8 file named `<descriptive-name>.scene.json`. The file contains
only valid JSON: no comments, Markdown fences, NaN, Infinity or trailing commas.
Do not overwrite an earlier user file while iterating; use numbered revisions.
Provide dependency files, a short explanation of the assumptions and exact open
and validation commands separately. Do not report a test as passed unless you
actually ran it and inspected its result.

## Accepted authoring subset

The installed native loader is authoritative. This intentionally compact subset
covers ordinary sandbox scenes. For advanced structures and effects, use shipped
recipes or editor-generated saves rather than guessing packet layouts.

- Root `format` is exactly `skullbonez.scene.json`; `version` is integer **9**.
  Required `cameras` is a nonempty array. Each camera needs `name`, `position`,
  `view` (a world-space look-at point), and `up`, the latter three exactly three
  finite numbers. Use `[0,1,0]` for up and distinct eye/view positions.
- `objects` is optional. Each supplied object needs a supported `type`, unique
  `name` (keep below 64 bytes), `position:[x,y,z]` and the shape fields below.
  Author a unique positive integer `sceneObjectId` from 1 through 4294967295.
  Version 8 can assign omitted IDs for migrated compact files, but explicit IDs
  make later editing and references stable. Never reuse IDs when rearranging rows.
- Coordinates are X/Z across the ground, Y up. Use metres, seconds, kilograms,
  linear velocity in metres/second and angular velocity in radians/second.
  Euler arrays use degrees; identity is `[0,0,0]`. State quaternions are
  `[x,y,z,w]`, identity `[0,0,0,1]`, using the current body-to-world convention.
  Prefer identity/Euler for hand authoring; do not copy pre-v3 state quaternions.
- `box`: required `halfExtents:[hx,hy,hz]`, `mass`, `restitution`. Half extents
  and mass must be positive finite numbers; restitution is in `[0,1]`. Optional
  `euler:[0,0,0]`, `velocity:[0,0,0]`, `fixed:false`. Full dimensions are twice
  the half extents. Put the centre at terrain height plus half-height.
- `ball`: required positive `radius`, `mass`, `moment` and `[0,1]` `restitution`.
  For a uniform solid sphere use `moment = 0.4 * mass * radius * radius`.
  Optional `euler`, `fixed`, `force:[0,0,0]` and
  `impulseWorldOffsetFromCenter:[0,0,0]`. Here `force` is a one-time initial
  impulse, not sustained thrust; the offset is a world-axis lever arm from the
  centre. To set exact initial velocity, use a `ballState`.
- `ballState`/`boxState`: required `position`, `velocity`, `angularVelocity`,
  `orientation`, `mass`, `restitution`, `inertia:[Ix,Iy,Iz]` and `radius` or
  `halfExtents`. Mass, dimensions and all three inertia components are positive.
  Required booleans `fixed` and `sleeping` (normally both false). Supply a normalized quaternion.
  For a uniform box, Ix = mass*(hy*hy+hz*hz)/3, and cyclic permutations for Iy/Iz.
  Never use zero mass to make a fixed body; use `fixed:true` with positive mass.
- `convexHull` uses `hull`, `position`, positive `mass`, `restitution`, optional
  `euler`, `velocity`, `angularVelocity`, `fixed`, `sleeping`. Built-in `hull`
  token `wedge` is available. Prefer the editor/catalog for other hull names.
  `convexHullState` has the same required state fields/inertia as a box state
  but `hull` replaces `halfExtents`. Missing hull data is a load error.
- All numbers must fit finite single-precision values. Do not treat an omitted
  optional value and an invalid supplied value as equivalent. Keep prototypes
  near `[500,30,500]` on the bundled terrain, with modest sizes/speeds. These
  are authoring recommendations, not invented parser limits.

Set `simulation.physics:true` to run dynamics; false freezes simulation. Optional
`timeScale` must be positive (default 1); `seed` is an unsigned integer.
`simulation.world` accepts `gravity` (Y acceleration, usually -9.81),
`fluidHeight` (world Y of water) and `fluidDensity` (nonnegative, 0 disables
buoyancy). Use the explicit values in the examples to avoid inherited settings.
`playback:{"frames":"unlimited","fixedStep":true}` gives interactive playback.
`editor:{"editableScene":true}` permits editing. These sections are optional;
include them for predictable new levels. Avoid developer solver/capacity settings.

Terrain is either `terrain:{"flatSlope":{"baseY":30,"slopeX":0,"slopeZ":0}}`
or `terrain:{"heightMap":"./my-terrain.heightmap"}`. Never supply both.
All three flatSlope numbers are required. Use the terrain brush and save to
produce heightmaps rather than inventing their encoding. Preserve the saved
sidecar. `debug.waterHidden:true` hides the water rendering; water height and
buoyancy are separate physical settings under `simulation.world`.

## Materials and the scene appearance

Use `cinematic:{"rendering":true,"styleModes":[22,16,14,5]}` to request the
current Split Gravity appearance: sky, terrain, object, water modes respectively.
Do not add a fictitious `splitGravity` or `twoTone` field. Per-object material
choices use the existing `objectMaterials` array, for example:

```json
{"target":"launcher","mode":"matte","color":[0.9,0.2,0.1],"roughness":0.72}
```

The target is the exact object name. Available mode names are `textured`, `matte`,
`metal`, `emissive`, `glass`, `toon`, `lowpoly`, `shadow`, `foliage`, `bark`,
`stone`, `ridge`, `shore`, `pine`. `color` is RGB; use `[0,1]` components.
`roughness`, `metallic`, `specular`, `transmission`, `stylization` each range
from 0 to 1. Optional `emissive` is RGB, `strength` is nonnegative. Omitted
properties retain the selected mode's parser defaults; specify the ones that
matter. Color and material mode are independent of physical mass/contact.
`terrain.material` accepts the same material properties without a target.
Ordinary objects show two-tone rotation panels by default, independently of their
finish. Missing `flags`, or a clear bit `2097152` (`0x200000`), means enabled.
To explicitly disable the cue, include `"flags":2097152` in that object's material.
When editing existing flags, set or clear only that bit and preserve other bits.
There is no separate `twoTone` JSON property. Material presets preserve this choice.
The existing integer flags field carries the setting; scene version 9 is unchanged.
Ground and specialised mapped celestial surfaces do not receive this object cue.
Do not invent other flags or a second color field. For example, a plain red metal:

```json
{"target":"launcher","mode":"metal","color":[0.9,0.2,0.1],"flags":2097152}
```

Validate both omitted-flags and explicit-off examples with the validation commands
below. After loading, save and reload in the editor and check that Two-tone still
matches the requested choice; changing the material finish must preserve it.

## Assets, interactions and portable files

`level-authoring/asset-catalog.json` lists exact asset names grouped by library.
For example `assetLibraries:["terrain_buggy"]` with
`assetInstances:[{"asset":"vehicle.terrain_buggy","name":"car","position":[500,32,500]}]`
creates the registered drivable buggy. Preserve its generated part IDs in later
saved revisions; do not hand-invent its vehicle state packet. The `buildings`
library includes walls, bridges, towers and stairs; `low_poly_nature` includes
rocks and trees. `physics_props` supplies `physics.disc_16`.

Bomb/tornado recipes are `effect.bomb` and `effect.tornado_anchor` in `buildings`.
Their runtime effect settings include typed saved packets. Placing a decorative
body is not proof of a working explosion or tornado. For timed effects and ragdoll
joints, place/configure them in the editor and save, or use a validated shipped
scene as the complete template. Do not fabricate the `timedFields` or vehicle
packet arrays. Initial velocity is directly supported and is the simplest way
to kick off a chain reaction. General custom scripts/triggers are not part of
this JSON authoring subset.

Asset libraries use `skullbonez.asset_library.json` (current version 3), styles
use `skullbonez.style.json` (current version 2). Bare library names select the
installed catalog. To freeze recipe dependencies, copy the exact shipped library
beside the scene and refer to `"./terrain_buggy.assets.json"`; the asset names
inside remain unchanged. Explicit `./` and `../` style/library paths resolve
beside their containing document. Heightmaps resolve beside the scene. Historical
`SkullbonezData/...` paths resolve from the application working folder. Custom
hull/texture references may still depend on that folder; include those files and
preserve their paths. Do not silently substitute a missing dependency.

Editor snapshots inline appearance and copy recipes/heightmaps to content-named
siblings. Share those siblings with the scene. Built-in hull/texture tokens still
require the installed app data. Our two basic examples need no external level
sidecars and can be copied outside the repository unchanged.

Opening supported old versions (1–9) does not rewrite their bytes. A save that
upgrades an old file retains `<level>.scene.json.v<version>-<content-id>.original`
beside it. To restore, close the level, copy that original over the scene, then
reopen. Preserve its old dependency files too. Future versions are rejected with
an update instruction; changing the version number by hand is not a migration.

## Generate, validate, repair, then play

1. Start with `level-authoring/minimal.scene.json`. For “a red launcher knocks
   over three blue blocks,” use `level-authoring/chain-reaction.scene.json`:
   launcher ID 101 starts at `[500,31,490]` moving +Z at 22 m/s; block IDs
   102–104 start at Z 499, 503, 507. The red launcher has mass 30 kg and the
   blue blocks 2 kg. Do not claim all three fall until a simulation confirms it.
2. Write your new file, retain the request and any dependency files, then run the
   installed validator. It uses the same C++ loader and asset resolution as the
   application, actually constructing the scene. It does not rewrite the input.
3. Read the JSON report's `accepted`, `unchanged`, `nativeExitCode`, `stdout` and
   `stderr`. Fix the actual diagnostic in a new revision while preserving intent,
   and repeat until accepted. Then perform the bounded gameplay check below.

Copyable commands (replace folder names, keep quotes). The validator sets the
native working folder to AppRoot, so you may run it from any folder:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Games\Skullbonez\tools\validate_level.ps1" -AppRoot "C:\Games\Skullbonez" -Scene "C:\Users\Me\Documents\My Levels\my-level.scene.json" -Report "C:\Users\Me\Documents\My Levels\reports\my-level-01.json"
$LASTEXITCODE
```

Exit **0** means native load accepted and input SHA-256 unchanged; **1** means
native load rejected; **2** means infrastructure, timeout or input-integrity
failure. The report and `.stdout.txt`/`.stderr.txt` siblings explain the result.
Use a fresh report name each run; existing reports are preserved. Default timeout
is 60 seconds. Missing app/data, missing runtime dependencies or unsupported GPU
are setup errors, not permission to delete the level. Typical content errors:
unsupported schema version; `box.mass must be > 0`; missing required field;
duplicate sceneObjectId; unresolved joint body; missing asset library/heightmap.

To open the accepted file with correct installed asset resolution:

```powershell
Set-Location "C:\Games\Skullbonez"
& ".\SKULLBONEZ_CORE.exe" --scene "C:\Users\Me\Documents\My Levels\my-level.scene.json"
```

Watch 5–10 seconds, inspect the intended objects, reset and edit as needed. A
successful load does not prove a bridge is stable or a course is drivable. Record
expected names/IDs/counts and measurable behavior, e.g. “launcher 101 advances
+Z and block 102 moves/rotates after impact.” Capture the result, not just an
input acknowledgement.

Where a developer Automation/Skarness build is available, use `tools/skarness.py`
to launch it, check `capabilities.get`, subscribe to `scene.objects`, resolve each
object by stable ID, step a bounded number of frames and resolve it again.
Retain the event stream and screenshots; stop with `session.stop`. The release
validator itself needs neither Python nor Skarness. If you cannot execute tools,
label the generated level **UNVALIDATED**, supply these commands and an explicit
expected-behavior checklist. Never invent a passed report.

Validator log paths append `.stdout.txt` and `.stderr.txt` to the complete report
filename, for example `validation.json.stdout.txt`.
