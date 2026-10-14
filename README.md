# kicad-visor-demo

## About

A working example of [kicad-visor](https://github.com/piruetasxyz/kicad-visor) by [piruetas](https://piruetas.xyz): on every push to `main`, a GitHub Actions workflow exports every KiCad project in this repository (schematics, board layers, 3D renders and seamlessly looping turntable videos) and publishes them as a website: <https://piruetas.xyz/kicad-visor-demo/>. Each board keeps its own license (see below).

## Acerca de

Ejemplo de [kicad-visor](https://github.com/piruetasxyz/kicad-visor), de [piruetas](https://piruetas.xyz). Cada vez que se hace push a `main`, un workflow de GitHub Actions exporta todos los proyectos KiCad de este repositorio y los publica como sitio web en <https://piruetas.xyz/kicad-visor-demo/>.

Por cada placa, el sitio muestra:

- el esquemático, en svg, png, jpg y pdf.
- la placa en 2D: frente, reverso, cobre y cada capa por separado.
- renders 3D: arriba, abajo, isométricas y perspectiva.
- videos turntable que se repiten sin cortes, en formato horizontal, vertical y cuadrado, sobre distintos colores de fondo.

## Placas

| placa | qué es | repositorio |
|-------|--------|-------------|
| [chufe](./chufe) | fuente de alimentación eurorack: entrada de 12 V DC, salidas ±12V y +5V | [piruetasxyz/chufe](https://github.com/piruetasxyz/chufe) |
| [chufebu](./chufebu) | bus de alimentación eurorack: 5 headers de 16 pines, cada uno con su conector Molex KK-396 | [piruetasxyz/chufebu](https://github.com/piruetasxyz/chufebu) |

Las placas son copias de sus repositorios, con la misma estructura de carpetas (`hardware/` y, en chufe, `terceros/`), para que las rutas de los modelos 3D y de las bibliotecas funcionen sin cambios. Para actualizar una placa, hay que copiar de nuevo su carpeta `hardware/` desde su repositorio.

## Cómo funciona

El workflow está en [.github/workflows/kicad-visor.yml](.github/workflows/kicad-visor.yml). Corre dentro de la imagen oficial `kicad/kicad:10.0-full` (KiCad 10 con sus modelos 3D), instala kicad-visor y ejecuta:

```bash
kicad-visor export . --output _site --only schematic,pcb,render,turntable
```

El resultado se publica directamente en GitHub Pages, sin hacer commit de los renders. Los frames de los videos quedan en caché entre ejecuciones: la primera vez se demora decenas de minutos por placa, y después solamente se vuelven a renderizar las placas que cambian.

Para usarlo con tus propias placas, sigue las instrucciones de [kicad-visor](https://github.com/piruetasxyz/kicad-visor#publishing-to-github-pages).

## Licencias

Cada placa conserva su propia licencia, en su carpeta: hardware bajo CERN-OHL-P-2.0 y documentación bajo CC-BY-SA-4.0. Ver [chufe/LICENSE.md](./chufe/LICENSE.md) y [chufebu/LICENSE.md](./chufebu/LICENSE.md). Los componentes de terceros de chufe, en `chufe/terceros/`, no son obra de piruetas: ver [chufe/LICENSES/LicenseRef-easyeda.txt](./chufe/LICENSES/LicenseRef-easyeda.txt).

## Acerca de piruetas

[piruetas](https://piruetas.xyz) es un estudio de arte chileno fundado en 2022 por [montoyamoraga](https://montoyamoraga.io), con base en Santiago de Chile.

- web: [piruetas.xyz](https://piruetas.xyz)
- github: [github.com/piruetasxyz](https://github.com/piruetasxyz)
- instagram: [@piruetas.xyz](https://instagram.com/piruetas.xyz)
