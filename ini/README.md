# Example scenes

Every subdirectory is self-contained:

- `*.ini` — scene descriptions (input for the engine)
- `filelist` — list of all `.ini` files in the folder; the engine reads it when run without arguments
- `*.L2D` — L-system definitions referenced by the L-system scenes
- `expected/` — reference renders (PNG) of what each scene should look like

Render a folder by running the engine from inside it (paths in the `.ini` files are relative to the working directory):

```bash
cd ini/l_systems
/path/to/engine          # or: /path/to/engine l_systems003.ini
```

The engine writes `<scene>.bmp` next to each `.ini`. Generated `.bmp` files are gitignored.

## Scene file format

Every scene starts with a `[General]` section whose `type` selects the renderer:

| `type` | Description |
| --- | --- |
| `IntroColorRectangle` | Red/green gradient rectangle |
| `IntroBlocks` | Checkerboard of colored blocks |
| `IntroLines` | Line-based figure: `QuarterCircle`, `Eye`, or `Diamond` |
| `2DLSystem` | Draws a 2D L-system from an `.L2D` file |
| `Wireframe` | 3D line drawing of one or more figures |
| `ZBufferedWireframe` | Wireframe with hidden-line removal via z-buffer |
| `ZBuffering` | Filled triangles with z-buffer |
| `LightedZBuffering` | Z-buffering with ambient/diffuse/specular lights |

### 2D L-system example

```ini
[General]
type = "2DLSystem"
size = 1000
backgroundcolor = (1, 1, 1)

[2DLSystem]
inputfile = 'dragon_curve.L2D'
color = (0, 0, 0)
```

The `.L2D` file defines the alphabet, draw function, replacement rules, initiator, angle, and number of iterations. Stochastic systems (see `l_systems_stochast/`) use a `StochasticRules` block where each symbol maps to multiple weighted replacements.

### 3D scene example

```ini
[General]
size = 1024
backgroundcolor = (0, 0, 0)
type = "Wireframe"
eye = (100, 50, 75)
nrFigures = 1

[Figure0]
type = "FractalTetrahedron"
nrIterations = 2
fractalScale = 3
scale = 1
rotateX = 0
rotateY = 0
rotateZ = 0
center = (0, 0, 0)
color = (1, 1, 1)
```

Figure types: `Cube`, `Tetrahedron`, `Octahedron`, `Icosahedron`, `Dodecahedron`, `Sphere`, `Cylinder`, `Cone`, `Torus`, `BuckyBall`, `3DLSystem`, `LineDrawing`, plus fractal variants (`FractalCube`, `FractalTetrahedron`, `FractalOctahedron`, `FractalIcosahedron`, `FractalDodecahedron`, `FractalBuckyBall`) and `MengerSponge`. Fractal figures take `nrIterations` and `fractalScale`.

## Folders

| Folder | Scenes | Highlights |
| --- | --- | --- |
| `intro/` | 5 | Color rectangle, blocks, line figures |
| `l_systems/` | 26 | Koch curves & snowflake, dragon curve, Sierpinski triangle/arrowhead, Hilbert & Peano curves, tree, spyrograph |
| `l_systems_stochast/` | 2 | Stochastic grass and circles — output differs per run |
| `3d_fractals/` | 178 | Fractal Platonic solids, buckyball, and Menger sponge in wireframe, z-buffered wireframe, and filled z-buffering; `expected/*_extra.png` are alternate reference renders |
