# AstoCAD-for-Debian13
AstoCad for Debian 13

Installing Astocad in Debian 13 is a little bit tricky. So here are the changes for a clean install

1.
Prerequisites
Before compiling, you need to grab the necessary development tools and libraries. The most efficient approach on Debian is to use apt build-dep to fetch all of FreeCAD's dependencies automatically.

Ensure your deb-src (source repositories) are enabled in /etc/apt/sources.list or /etc/apt/sources.list.d/debian.sources.

2.
sudo apt update
sudo apt install build-essential cmake git

# Fetch all FreeCAD build dependencies
sudo apt build-dep freecad

sudo apt install qt6-base-dev qt6-svg-dev qt6-tools-dev qt6-webengine-dev libpyside6-dev libshiboken6-dev pyside6-tools pyqt6-dev-tools python3-dev

sudo apt update
sudo apt install qt6-base-private-dev

3.
AstoCAD's source code is hosted on GitHub. Make sure to include the --recurse-submodules flag to pull in all necessary sub-components.

git clone --recurse-submodules https://github.com/AstoCAD/FreeCAD.git AstoCAD-src
cd AstoCAD-src

4.
Copy the attached CMakeLists.txt to your astrocad directory: your astrocad_source/src/3rdParty/customtitlebarkit/CMakeLists.txt

5.
Copy the attached PolarPatternExtension.cpp to your astrocad directory: your astrocad_source/src/Mod/Part/App/PolarPatternExtension.cpp

Copy the attached PolarPatternExtension.h to your astrocad directory: your astrocad_source/src/Mod/Part/App/PolarPatternExtension.h

Copy the attached LinearPatternExtension.cpp to your astrocad directory: your astrocad_source/src/Mod/Part/LinearPatternExtension.cpp

Copy the attached LinearPatternExtension.h to your astrocad directory: your astrocad_source/src/Mod/Part/LinearPatternExtension.h


6
Configure the Build
It is best practice to keep your build files separated from the source code by building out-of-source.

mkdir build
cd build
cmake ..

7.
Compile

make -j$(nproc)

8.
Run AstoCAD
Once the build completes without errors, there is no need to install it globally unless you want to. You can run the executable directly from the bin directory:

./bin/FreeCAD

(Note: AstoCAD runs under the FreeCAD binary name, but you will see the customized AstoCAD UI and toolsets once it launches).

