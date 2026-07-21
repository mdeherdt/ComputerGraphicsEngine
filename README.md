# ComputerGraphicsEngine

A C++14 computer graphics engine for generating a wide range of images from `.ini` configuration files.

It supports 2D intro patterns, 2D L-systems, wireframes, Z-buffered wireframes, Z-buffering, and lighted Z-buffering, plus generating and transforming common 3D figures such as cubes, tetrahedra, spheres, cylinders, cones, and tori.

## Features

- **2D rendering**
  - Intro patterns like rectangles, blocks, and line-based compositions
  - 2D L-system drawing with deterministic and stochastic rules
- **3D rendering**
  - Wireframes
  - Z-buffered wireframes
  - Filled Z-buffering
  - Lighted Z-buffering
- **Figure generation**
  - Platonic solids
  - Cone, cylinder, sphere, torus
  - Fractal generation helpers
- **Output**
  - Renders images to BMP files

## Examples

_Add screenshots here once you generate a few representative renders._

Suggested examples:

- 2D intro image
- L-system output
- Wireframe object
- Z-buffered object
- Lighted 3D scene

If you add images, a simple layout like this works well:

```md
![Wireframe example](docs/images/wireframe.png)
![Lighted example](docs/images/lighted-scene.png)
```

## How it works

The executable reads one or more `.ini` files and generates corresponding `.bmp` images.

If you do not pass arguments, it looks for a `filelist` file and processes the entries inside it.

## Build

This project uses CMake.

```bash
cmake -S . -B build
cmake --build build
```

## Run

```bash
./engine path/to/config.ini
```

Or, if you have a `filelist` file:

```bash
./engine
```

## Project structure

- `src/` — engine implementation and rendering modules
- `l_systems_stochast/` — L-system related resources
- `CMakeLists.txt` — build configuration

## Notes

- The project currently targets **C++14**.
- Generated output images are written as `.bmp` files.
- A few image assets in the README would make the repo much more attractive and easier to understand.

## Good screenshots to add

If you want the README to look polished, I recommend adding:

1. A clean wireframe render
2. A Z-buffered render
3. A lighted render
4. One interesting L-system image

A good folder layout would be:

```text
docs/images/
```

Then reference them from the README using relative paths.
