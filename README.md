# Qucs-RFlayout
A tool to produce layouts from Qucs RF schematic (microstrip only for now)

`qucs-schematic.sch` -> `kicad-layout.kicad_pcb` [OK]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-> `kicad-module.kicad_mod` [OK]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-> `pcb-rnd-layout.lht` [OK]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-> `openEMS-script.m` [Alpha]

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-> `gmsh.geo` [ASAP]

<br>

French documentation [here](https://github.com/thomaslepoix/ESTEI/blob/master/M2_CPP_Qucs-RFlayout/Qucs-RFlayout.pdf)

<br>

## Screenshots

### Qucs : schematic.sch
![qucs_sch](res/preview_qucs_sch.png)

### Qucs-RFlayout : preview
![qucsrflayout_preview](res/preview_qucsrflayout.png)

### Pcbnew : layout.kicad_pcb
![pcbnew_kicad_pcb](res/preview_pcbnew_kicad_pcb.png)

### Pcbnew : module.kicad_mod
![pcbnew_kicad_mod](res/preview_pcbnew_kicad_mod.png)

### Pcb-rnd : layout.lht
![pcb-rnd_lht](res/preview_pcb-rnd_lht.png)

### OpenEMS : simulation.m
![appcsxcad_m](res/preview_appcsxcad_m.png)

<br>

## Build & Install

- With CMake (You must use a modern version >= 3.11) :

```sh
Qucs-RFlayout $

    mkdir build && cd build

    cmake ..
    make

    # Prefered way : use your packet manager
    make package
    sudo apt-get install ./qucsrflayout_*.deb    # Debian
    sudo dnf install ./qucsrflayout-*.rpm        # Fedora

    # Classic way : install manually
    sudo make install
```

- Or if you don't have CMake, you can use QMake :

```sh
Qucs-RFlayout $

    mkdir build && cd build

    qmake ..
    make
    sudo make install
```

<br>

## Usage

```
qucsrflayout -i qucs-schematic.sch -o output-directory -f .output-format
```

<br>

## Limitations

- Microstrip only for now, coplanar waveguide ASAP.
- Any other component cannot be converted into a geometric shape of metal by this tool.
- Use one wire to connect only two components ports, use apropriate components to make tees or crosses.
- Equations are not supported yet, avoid using variables in component fields.
- QucsStudio schematics are supported but it is closed source and there are some incompatibilities so please prefer using Qucs.

<br>

Work in progress... thomas.lepoix@protonmail.ch
