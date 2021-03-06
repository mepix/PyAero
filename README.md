
# PyAero ![](docs/images/RAE2822.png)

[![readthedocs](https://img.shields.io/badge/docs-latest-brightgreen.svg?style=flat)](https://pyaero.readthedocs.io/en/latest/?badge=latest)
[![GitHub](https://img.shields.io/github/license/mashape/apistatus.svg)](https://en.wikipedia.org/wiki/MIT_License)


PyAero is an open-source airfoil contour analysis and CFD meshing tool written in Python. The graphical user interface is written in Qt for Python (PySide2).

## Features

 - Load and display airfoil contour files
 - Airfoil splining and refining
   - Get a smooth contour and sufficient contour points
   - Refine leading and trailing edge resolution
   - Prepare contour for meshing
   - Automatic calculation of leading edge radius
   - Point distribution on spline used as mesh distribution
 - Automatic generation of block-strcuctured mesh
   - Currently single element C-type mesh
   - Strictly orthogonal mesh in the vicinity of the airfoil
   - Mesh resolution control for airfoil, leading edge, trailing edge and windtunnel
 - Sharp or blunt trailing edges
 - Mesh smoothing (to be improved)
 - Mesh export
   - [AVL FIRE](https://www.avl.com/fire) (.flma)
   - [SU2](https://su2code.github.io/) (.su2)
   - [GMSH](http://gmsh.info) (.msh)
   - Automatic definition of boundary elements (edges, faces)
     - Airfoil, inlet, outlet, symmetry
 - Simple aerodynamic analysis using [AeroPython](http://nbviewer.ipython.org/github/barbagroup/AeroPython/blob/master/lessons/11_Lesson11_vortexSourcePanelMethod.ipynb)
 - Airfoil contour analysis (gradient, curvature and curvature circle)
 - NOT YET IMPLEMENTED: Advanced aerodynamic analysis
   - Linking to open source CFD software (e.g. SU2)

## Sample screenshots

![](docs/images/gui_airfoil1_new.png)
**PyAero GUI at a glance**
<br><br>

![](docs/images/mesh_888x260_RAE2822.gif)
**Example mesh around RAE2822 airfoil**
<br><br>

![](docs/images/LE_mesh_888x382_RAE2822.png)
**Example mesh around RAE2822 airfoil - Leading Edge**
<br><br>

![](docs/images/TE_mesh_RAE2822.png)
**Example mesh around RAE2822 airfoil - Trailing Edge (with finite thickness)**
<br><br>

![](docs/images/TE_mesh_sharp.gif)
**Example mesh with a sharp Trailing Edge**
<br><br>

![](docs/images/MAKAROV_KPS_mesh.gif)
**Example mesh around MAKAROV KPS airfoil as used in the CFD code AVL-FIRE.**
<br><br>

![](docs/images/MAKAROV_KPS_Veloyity.gif)
**Velocity field (RE=50000) around MAKAROV KPS airfoil using the CFD code AVL-FIRE.**
<br><br>

![](docs/images/MAKAROV_KPS_TKE.gif)
**Turbulence kinetic energy field (RE=50000) around MAKAROV KPS airfoil using the CFD code AVL-FIRE.**
<br><br>

![](docs/movies/RG14_3D_laminar_Iso-Q_pressure.gif)
**Unsteady laminar 3D calculation of the RG14 airfoil using the CFD code AVL-FIRE.**
<br>
**RE=330000, AOA=2°, 20 million cells.**
<br>
**Laminar calculation: CD=0.0079, CL=0.371**
<br>
**LES calculation (Kobayashi SGS): CD=0.0078, CL=0.362**
<br><br>

## Documentation

The PyAero documentation can be found at the following link:

**[http://pyaero.readthedocs.io](http://pyaero.readthedocs.io)**

The documentation is automatically generated using the markdown files in the [docs](https://github.com/chiefenne/PyAero/tree/master/docs) folder via [Sphinx](http://www.sphinx-doc.org/en/stable/index.html).

## Dependencies

 - [Python 3.x](https://www.python.org/)
 - [Qt for Python (PySide2) 5.11.x](https://www.qt.io/qt-for-python)
 - [Numpy](http://www.numpy.org/)
 - [Scipy](https://www.scipy.org/)

At the moment a binary is available for Windows. On other platforms the source code needs to be copied to your computer. Of course it can be done on Windows as well.

## Download

### Option 1: Download Windows executable:

> NOTE: Currently the Windows executable is not up to date

Go to the [Windows](https://github.com/chiefenne/PyAero/tree/master/Windows) folder and download *PyAero.zip*. Extract that file in an arbitrary location on the PC. There will be a file and a folder extracted, *PyAero.exe* and *data* respectively.
Run PyAero by double-clicking the executable.

### Option 2: Download source version using Git:
The $ symbol represents the prompt at command shell. It is not part of the command.

```bash
$ cd anywhere_on_your_computer
$ git clone https://github.com/chiefenne/PyAero.git
```

### Option 3: Download source version as a ZIP file:

From the [PyAero GitHub repository](https://github.com/chiefenne/PyAero). There is on the upper right side a green pull down menu "Clone or download". Click on it and then click "Download ZIP". You get a file "PyAero-master.zip" which you store anywhere on your computer.

```bash
$ cd anywhere_on_your_computer
$ unzip PyAero-master.zip
```

## Installation

After cloning from Git, or downloading and unzipping, set the environment variable for the PyAero installation path.

### Linux and Cygwin

```bash
$ setenv PYAERO_PATH path_to_your_installation
```

Run PyAero using:

```bash
$ python $PYAERO_PATH/src/PyAero.py
```

To simplify the command, set an *alias*.

```bash
$ alias pyaero  "python $PYAERO_PATH/src/PyAero.py"
```

Then start PyAero using simply:

```bash
$ pyaero
```

To keep everything stored across sessions, you might want to add PYAERO_PATH and the *alias* command to your *~.bashrc, ~/.profile* or similar depending on your environment.

### Windows

#### If runnining the binary:

See [download option 1](#option-1-download-windows-executable).

#### If running from source:

In a cmd shell type (if the installation is on drive *D:* in the folder *My_PyAero_Installation_Path*):

```bash
$ set PYAERO_PATH=D:/My_PyAero_Installation_Path
```

Since this stores the PYAERO_PATH variable only for the current seesion, you can aslo press the Win+Pause keys and then open the advanced tab to set the PYAERO_PATH environment variable there to keep it also after reboot.

Run PyAero using from a cmd shell (if python is installed in "c:/python3"):

```bash
$ c:/python3/python.exe %PYAERO_PATH%/src/PyAero.py
```

You should be good to go.

## Qt for Python version (PySide2)

PyAero version based on the **Qt for Python (alias PySide2)** GUI API

**Reasoning for going with Qt for Python**

PyAero started based on the PyQt4 which for me was the API to go at the time when I started development. PyAero two years ago achieved an 80% state.

After a small creative break I decided to upgrade to PyQt5 and continue development. I soon realized that the PyQt5 documentation lacks information, i.e. there were only links to the Qt C++ documentation and no Python related docs, I had the feelig that the PyQt5 development probably stagnates.

Short online research revealed to me that meanwhile Qt themselves are developing now **Qt for Python (alias PySide2)** which is based on the legacy Pyside API. This made me think that it is possibly best to go with Qt for Python as it is tightly coupled to Qt.

## For the brave

<a href='https://ko-fi.com/G2G6143T6' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi4.png?v=2' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

Andreas Ennemoser – andreas.ennemoser@aon.at

Distributed under the MIT license. See [LICENSE](https://raw.githubusercontent.com/chiefenne/PyAero/master/LICENSE) for more information.
