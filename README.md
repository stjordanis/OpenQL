# OpenQL Framework #

OpenQL is a C++ framework for high-level quantum programming. The framework provides a compiler for compiling and optimizing quantum code. The compiler produce the intermediate quantum assembly language and the compiled micro-code
for various target platforms. While the microcode is platform-specific, the quantum assembly code (qasm) is hardware-agnostic and can be simulated on the QX simulator.

## Supported Patforms

* Linux
* Windows
* OSX

## Required Packages

* g++ compiler with C++11 support (Linux)
* MSVC 2015 with update 3 (Windows)
* cmake
* swig
* python 3.5
* [Optional] pytest used for running tests
* [Optional] Graphviz Dot utility to convert graphs from dot to pdf, png etc
* [Optional] XDot to visualize generated graphs in dot format

## Notes for Windows Users
* Use Power Shell for installation
* Set execution policy by:

        Set-ExecutionPolicy -ExecutionPolicy RemoteSigned

* Install [PowerShell Community Extensions](https://www.google.com "PowerShell Community Extensions")
* MSVC 2015 should be added to the path by using the following command:

        Invoke-BatchFile "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64
* To make your life easier, you can add this command to the profile you are using for power shell, avoiding the need to manually run this command every time you open a power shell. You can see the path of profile by `echo $PROFILE`. Create/Edit this fille to add the above command.

* Python.exe and swig.exe should be in the path of power shell. To test if swig.exe is the path, run:

        Get-Command swig

* Make sure the following variables are defined:
  * PYTHON\_INCLUDE (should point to the directory containing Python.h)
  * PYTHON\_LIB (should point to the python library python35.lib)

# Getting started 

After installing OpenQL (see install instructions below) a good place to get started is by looking at the files in the "tests" directory, e.g., test_basics.py. Here you can find commented examples on how to use OpenQL. 

N.B. gates in OpenQL are *case insensitive*. 



# Compiling C++ OpenQL tests and programs

Existing tests and programs can be compiled by the following instructions. You can use an existing example as a starting point and write your own programs. Make sure to include them in CMakeLists.txt file to inform cmake to compile it as well.


## Linux/OSX
    mkdir cbuild 
    cd OpenQL/cbuild 
    cmake ..   # generates the make file based on CMakeLists.txt in the OpenQL directory
    make       # compiles the source code into the current directory. 

To execute an example program go to e.g., `OpenQL/cbuild/programs` and execute one of the files e.g.,  `./simple`. The output will be saved to the output directory next to the file.

If one wants to compile and run a single file, e.g., `example.cc`, to compile it one can run : 
```
    mkdir output           # create an output directory if it does not exist
    g++ -std=c++11 example.cc -o example.exe -I OpenQL/   # compile the file
    ./example.exe                                         # execute the file
```

## Windows
    cd OpenQL/cbuild
    cmake -G "NMake Makefiles" ..
    nmake


## Usage

Example C++ tests and programs can be found in 'tests' and 'programs'
directories. Executables for these will be generated in 'build/tests' and 'build/programs'
directory.

Example python tests and programs can be found in the 'tests' and 'programs' directories.
These can be executed as 'python tests/simplePyTest.py'.

# Installing OpenQL as Python Package

N.B. the instructions below will compile the C++ files the first time they are run. 
If you are updating an existing installation you should first clean and recompile the C++ files using the following command. 
```
    rm -rf build cbuild       # delete the old build folders
```

## Linux, Windows & OSX

Running the following command in Terminal/Power Shell should install the openql package:

        pip install  -e .

# Running the tests

Run `py.test -v` to test the installation. In order to pass all the tests, `qisa-as` inside `tests` directory should be installed first. Follow the instructions in `tests/qisa-as/README.md` to install `qisa-as`.
