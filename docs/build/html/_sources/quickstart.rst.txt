Quick Start
***********
Below, we describe how to setup FOBOS hardware and software and test that everything is working.

Requirements
============
1. Digilent Basys3 board
2. A PC with Linux installed
3. Python2 installed
4. Xilinx Vivado 2017.2

Software Installation
=====================

Note: The following installation procedure is tested on Linux Ubuntu 16.04.

1. Download FOBOS from the `FOBOS home page <https://cryptography.gmu.edu/fobos/getfobos.php>`_.
2. Extract the archive into the directory of your choice

.. code-block:: bash

    $ tar xvfz fobos-v2.0.tgz

3. Use the following commands to install the necessary Python packages:

.. code-block:: bash

    $ sudo apt-get install python-pip
    $ sudo pip install numpy
    $ sudo pip install pyserial
    $ sudo pip install matplotlib
    $ sudo pip install scipy
    $ sudo pip install configparser

Hardware Setup
==============

1. Build the control board Vivado project.

.. code-block:: bash

    $ cd path-to-fobos/capture/ctrl/basys3ctrl/vivado
    $ make

2. Open the project created using Vivado

.. figure::  figures/open_project.png
   :align:   center

   Open Vivado project

3. In the Flow Navigator window, click 'Generate Bitstream'.
4. After bitstream is generated, click File > Export > Export Hardware ... make sure to select 'Include bitstream'.

.. figure::  figures/export_hardware.png
   :align:   center

   Export Hardware

5. Launch the Xilinx SDK (File > Launch SDK).

.. figure::  figures/launch_sdk.png
   :align:   center

   Launch SDK

6. In the SDK, create a new empty project(File> New application project). You will need to select the hardware platform.
   SDK will create the BSP project from the hardware platform and create the empty project.

.. figure::  figures/create_sdk_app.png
   :align:   center

   Create Project

6. Link all the .c and .h files in the fobos/sources/basys3ctrl/sdk/src to the project 
   (right-click on (project/src) -> Import -> General-> file system -> browse to file). 
   make sure to check "Advanced-> Create links in the workspace" and "Create virtual folders" .

.. figure::  figures/import_sdk_src.png
   :align:   center

   Launch SDK

7. Right-click on the project you just created and select Build Configurations > Set Active > Release. Then right-click again and select Build Project.
8. Make sure that there are no debug flags. Right-click the release folder under the project and select Properties. In the window that appears
select C/C++ Build > Settings > Microblaze gcc Compiler > Debugging and set Debug Level to 'None'.


.. figure::  figures/release_settings.png
   :align:   center

   Remove Debugging