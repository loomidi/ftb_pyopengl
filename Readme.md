
About PyOpenGL

PyOpenGL is the most common cross-platform Python binding to OpenGL and related APIs. The binding is created using the standard ctypes library and is provided under an extremely liberal BSD-style Open-Source license.
PyOpenGL Supports:
 * OpenGL v1.1 to 4.4
 * GLES 1 to 3.1 (Experimental)
 * GLU
 * EGL, WGL, GLX
 * GLUT, FreeGLUT
 * GLE 3 (GL Extrusion Library)
 * Hundreds of extensions to GL, GLES, EGL, WGL, and GLX
PyOpenGL is interoperable with a large number of external GUI libraries for Python including (but not limited to):
 * wxPython
 * PyGame
 * PyQt and PySide
 * PyGTK
 * Raw XLib
 * OSMesa
 * Raspberry Pi BCM
 * Tkinter (if you have installed the Togl widget for Tk)
PyOpenGL 3.x runs on:
 * Python 3.3+ (3.2 support is likely to work, but untested)
 * Python 2.7 (recommended)
 * Python 2.6 (for compatibility with older software and systems)
 * PyPy (experimental)
Sub-Packages:
The PyOpenGL project includes a number of sub-projects:
 * PyOpenGL: The "OpenGL" package when installed, provides GL, GLES1, GLES2, GLES3, GLUT, GLU, GLE, WGL, EGL, and GLX subpackages.
 * OpenGL_accelerate: A Cython-coded accelerator module for PyOpenGL, optional, but recommended where available. The code for OpenGL_accelerate is in the core PyOpenGL repository, but is distributed as a separate Python package and installs as OpenGL_accelerate.
 * PyOpenGL-Demo: A collection of small stand-alone demos. You normally want to run these from the source distribution, as there's nothing installed by the package.
 * OpenGLContext: A teaching and testing library built on top of PyOpenGL (and a lot of other libraries). You do NOT need OpenGLContext to use PyOpenGL.
Downloading and Installation:
The easiest way to install PyOpenGL is using pip:
$ pip install PyOpenGL PyOpenGL_accelerate

You can also manually download the packages from PyPI:
 * PyOpenGL
 * PyOpenGL_accelerate
 * PyOpenGL Demo
 * OpenGLContext
Unpack them into temporary directories, change to those directories, and run:
python setup.py install

Detailed installation instructions are available.
Documentation:
The documentation collection provides reference documentation, support and feedback information, and pointers to more in-depth documentation.
Architectural Overview
The project is built on a pure PyOpenGL architecture for maximum performance and control, leveraging NumPy for efficient 3D grid computations. Interaction with the AI entity cluster is currently managed via terminal commands, which directly influence the cellular automaton's rules and cell properties.
Installation (for Termux / Android)
To run this project on your Android device using Termux, follow these steps. This setup requires a VNC server to display the graphical output.
1. Update Termux and Install Core System Packages:
pkg update && pkg upgrade -y
pkg install -y python git clang python-dev openblas libjpeg-turbo libpng libtiff freetype zlib libgl glut pkg-config

 * python: The Python interpreter.
 * git: For cloning the repository.
 * clang: The C/C++ compiler needed for some Python packages.
 * python-dev: Python development headers.
 * openblas: Optimized linear algebra library for NumPy.
 * libjpeg-turbo, libpng, libtiff, freetype, zlib: Libraries for image and font processing (needed by Pillow).
 * libgl, glut: Core OpenGL and GLUT (OpenGL Utility Toolkit) libraries for rendering.
 * pkg-config: Helps find system libraries during compilation.
2. Install VNC Server (for Graphical Output):
pkg install -y x11-repo tigervnc

3. Install Python Libraries (Leveraging Termux's Pre-built Packages):
# Install NumPy and Pillow using Termux's pre-built Python packages
pkg install -y python-numpy
pkg install -y python-pillow

# Install PyOpenGL (PyOpenGL_accelerate is optional and can be skipped if it causes issues)
pip install PyOpenGL PyOpenGL_accelerate

 * Important: python-numpy and python-pillow from pkg are pre-compiled for Termux, avoiding common compilation errors. PyOpenGL_accelerate is optional for performance; if it fails, you can omit it.
4. Start VNC Server and Connect:
vncserver

 * Set a password if prompted. Note the display number (e.g., :1).
 * On your Android device, download a VNC client (e.g., VNC Viewer) and connect to localhost:<display_number> (e.g., localhost:1).
How to Run the Visualizer
 * Navigate to Project Directory:
   cd /path/to/your/ftb_pyopengl_folder

   (Replace /path/to/your/ftb_pyopengl_folder with the actual path where you cloned/saved the repository).
 * Run the Python Script:
   python main.py

   (Assuming your main code file is named main.py).
Interaction
 * 3D Visualization: A PyOpenGL window will appear in your VNC client showing the 3D cellular automaton.
 * Camera Controls:
   * Mouse Drag: Rotate the camera.
   * w key: Zoom in.
   * s key: Zoom out.
 * AI Chat Interaction (via Terminal): Type commands into the Termux terminal where you launched the script.
   * set birth X Y Z: Sets birth rules (e.g., 'set birth 3 6').
   * set survival X Y Z: Sets survival rules (e.g., 'set survival 2 3').
   * assign roles: Randomly assigns roles (Generator, Stabilizer, etc.) to live cells.
   * randomize grid: Resets the grid to a new random state.
   * dimensional fold or warp: Triggers a grid reset/reconfiguration.
   * status: Get a report on live cells and role distribution.
   * hello
 * Exit: Press the ESC key in the PyOpenGL window.
Detailed PyOpenGL/Dependency Information
This section provides additional context and advanced installation notes for PyOpenGL and its common dependencies, derived from the official PyOpenGL documentation.
Most users of PyOpenGL should use pip to install PyOpenGL automatically. It can be installed either to the system Python or a Virtualenv.
$ pip install PyOpenGL PyOpenGL_accelerate

Manual Installation
If you cannot, or would prefer not to, use pip, you can download the package from PyPI:
 * PyOpenGL
 * PyOpenGL_accelerate
 * PyOpenGL Demo
The package uses Setuptools for its installation.
$ tar -zxvf PyOpenGL-3.1.0.tar.gz
$ cd PyOpenGL-3.1.0
$ python setup.py install

Note that you will require a working C compiler to compile the PyOpenGL-accelerate package. Pre-built packages are available for MS Windows 32 and MS Windows 64 users.
$ tar -zxvf PyOpenGL-accelerate-3.1.0.tar.gz
$ cd PyOpenGL-accelerate-3.1.0
$ python setup.py install

Recommended Enhancements for PyOpenGL
 * Numpy: Essential for numerical operations and grid management.
 * GLUT or FreeGLUT: Provides windowing and interaction capabilities. Available as an rpm/deb/ebuild for most modern Linux machines. The Win32 and Win64 binary installers for PyOpenGL include a copy of GLUT.
 * Python Imaging Library (PIL) (Pillow): Any recent version. Used for image processing, including potential texture generation.
 * GLE: The GL Extrusion library, available on most Linux distributions (libgle3). The Win32 package of PyOpenGL includes a copy of GLE compiled as a DLL.
 * Note: Togl support is deprecated. It's there for legacy code (once you compile Togl), but you should choose a GUI library that has OpenGL support built-in for any new development. Togl support has been dropped due to the complexity of compilation and the headache of maintenance. There are projects which attempt to provide Togl support; feel free to install those into your Python's Tk installation if you need Togl under Python.
OpenGLContext Installation
OpenGLContext is a very large package that depends on a large number of other packages to function. You do NOT need OpenGLContext to work with PyOpenGL.
Basic installation of OpenGLContext is as follows (note that you must explicitly specify the OpenGLContext and PyVRML97 releases as they are not currently in final/production releases on PyPI):
$ virtualenv oglc-env
$ source oglc-env/bin/activate
(oglc-env)$ pip install PyOpenGL PyOpenGL_accelerate "PyVRML97==2.3.0a4" simpleparse numpy "OpenGLContext==2.2.0a3" pydispatcher pillow

Once you have the dependencies, you can install OpenGLContext itself:
$ pip install PyDispatcher PyVRML97 OpenGLContext

Recommended Enhancements for OpenGLContext
 * TTFQuery and FontTools: Provide access to TrueType fonts stored in the file system, used by the "toolsfont" and "pygamefont" modules in the scenegraph/text package. Without these modules, you will not have access to extruded fonts (toolsfont) or antialiased bitmap fonts (pygamefont).
 * wxPython and/or PyGame: Additional contexts/windowing environments; only GLUT contexts are available otherwise. PyGame also provides antialiased bitmap fonts, while wxPython can provide aliased bitmap fonts if necessary.
 * win32all: win32ui and win32con provide support for WGL-based polygonal text, only available for Win32 systems of course. The WGL polygonal text is not used by the scenegraph engine, so it is not required for anything save playing with the WGL polygonal text demonstration module.
Further Reading and References
This section provides general background and links to more in-depth documentation for OpenGL and its Python bindings.
General Background
OpenGL under Python is largely the same as OpenGL under most other languages, so you can use much of the documentation you'll find around the Internet, or in your local bookstore. This page primarily provides links to PyOpenGL-specific documentation. Users of OpenGLContext should also see the OpenGLContext documentation page.
References
These documents tend to focus on the particular APIs and details of operation for PyOpenGL (or OpenGL in general).
 * Installing PyOpenGL and OpenGLContext -- building and installing the two libraries from binary or source distributions
 * PyOpenGL for OpenGL Programmers -- quick introduction to various features of PyOpenGL not normally found in OpenGL programming texts (e.g. strict exception handling, function aliases, array/pointer methods with Numpy)
 * PyOpenGL 3.x Reference -- automatically generated versions of the OpenGL programming reference with Python-specific call-signature annotations for PyOpenGL 3.x series. These are the OpenGL man-pages with PyOpenGL-specific annotations. The man pages also contain links to real-world PyOpenGL source-code which uses the described entry points.
   * GL Reference
   * GLU Reference
   * GLUT Reference
   * GLE Reference
 * Contributing -- guide to how to help develop PyOpenGL
 * MSDN's OpenGL Platform SDK (including WGL documentation)
 * SGI OpenGL Extension Registry -- where to go to look up an OpenGL extension's semantics and interfaces
 * OpenGL.org specification collection -- official specifications for OpenGL, GLU and GLUT
 * PIL Handbook -- Image handling library for Python
 * Numpy Documentation -- documentation for the multi-dimensional array-handling extension
