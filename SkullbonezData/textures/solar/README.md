# Planetary textures

Planet, Sun, Moon, Earth layer, ring and star maps by Solar System Scope / INOVE:
https://www.solarsystemscope.com/textures/

Licensed under Creative Commons Attribution 4.0 International:
https://creativecommons.org/licenses/by/4.0/

The provider's maps combine NASA imagery with adjusted colour and inferred
terrain where imagery is missing. They are visual maps, not scientific datasets.

`python tools/build_solar_textures.py` downloads source files into the local
TestOutput cache and creates surfaces.jpg plus sources.json. The shipped atlas
resamples and packs the originals with wrap/clamp gutters. The manifest records
the source URLs, source hashes, atlas hash and exact tile layout. Attribution
must accompany redistribution of these texture assets.

The GPU atlas is 16384 x 16384 RGBA8 with 64-pixel wrap/clamp gutters.
Earth day/cloud/specular/normal maps and the shared Moon map occupy 8192 x 4096
tiles; the other eleven tiles are 4096 x 2048. `sources.json` records each
rectangle. Source file names do not guarantee their decoded resolution.

The disk asset uses JPEG quality 98 without chroma subsampling. Ring optical
density is packed into blue; the shader reconstructs its neutral warm colour
from red and green. This preserves the large GPU texture while keeping the
individual repository asset below the repository file-size limit.

Use `--offline` to rebuild from cached sources. All satellites share Earth's
Moon map. Base GPU storage is 1 GiB before mipmaps (about 1.33 GiB with mips);
loading remains restricted to scenes requesting spherical materials.
