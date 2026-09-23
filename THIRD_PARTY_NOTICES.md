# Third-party notices

SkullbonezCore uses third-party components that retain their own licenses.
The SkullbonezCore Noncommercial License does not restrict rights granted by
those licenses or impose royalties on the third-party material itself.

This repository contains public attribution documents, not the engine or vendor
source. Each future release must include the license texts and notices applicable
to the components and assets it actually distributes. This inventory is not a
complete license inventory for an unpublished build.

## Box3D deterministic math

- Upstream: <https://github.com/erincatto/box3d>
- Adapted revision: `30c67b5e6d0a3a66f0f506c69ce9e9e0587e3b7c`
- Adapted algorithms: `b3ComputeCosSin` and `b3Atan2` from `src/math_functions.c`
- Copyright: 2026 Erin Catto
- License: [MIT](ThirdPtySource/box3d_math_LICENSE.txt)

## Solver2D sample scenes

- Upstream: <https://github.com/erincatto/solver2d>
- Adapted revision: `1e0492d81f68c7831cfa549699dd98bcb8454060`
- Adapted sample files: `sample_contact.cpp`, `sample_joints.cpp`, and `sample_far.cpp`
- Copyright: 2024 Erin Catto
- License: [MIT](ThirdPtySource/solver2d_samples_LICENSE.txt)

## SMAA

- Upstream: <https://github.com/iryoku/smaa>
- Revision: `71c806a838bdd7d517df19192a20f0c61b3ca29d`
- Authors: Jorge Jimenez and coauthors
- License: [SMAA license](ThirdPtySource/SMAA/LICENSE.txt)

## Planetary textures

Solar System Scope / INOVE maps are licensed under Creative Commons Attribution
4.0 International. See the [attribution](SkullbonezData/textures/solar/README.md)
and [source and modification record](SkullbonezData/textures/solar/sources.json).

## Other dependencies and assets

See the [dependency information](ThirdPtySource/README.md). Runtime DLLs, fonts,
and other assets may have separate terms; consult the notices accompanying the
particular release.
