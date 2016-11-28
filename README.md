MetaSim2.0: Event-based simulator
=================================
A new version of the metasim library slightly redesigned

Authors: Giuseppe Lipari, Gerardo Lamastra, Antonino Casile, 
         Luigi Palopoli, Cesare Bartolini

Contributors: Luca Abeni, Marco Caccamo, Fabio Rossi, Claudio Scordino,
			Fabio Cremona, Matteo Morelli, Andrea Parri

Copyright: Retis Laboratory, Scuola Superiore Sant'Anna
email:     g.lipari@sssup.it

This is open source software and is distributed under the terms of the Gnu
Public License (GPL). See COPYING for more details.

======================================================================

SUMMARY

1. INTRODUCTION
2. RELEASE NOTES
3. COMPILING
4. INSTALLING
5. RUNNING THE EXAMPLES
6. ADD A NEW EXAMPLE
7. BUGS AND CONTRIBUTIONS

======================================================================

## 1. INTRODUCTION

MetaSim2.0 is a library for discrete event simulation written in C++. It
has been developed as an internal project at Scuola Superiore
Sant'Anna as part of many research project, mainly thanks to the work
of many PhD students.


## 2. RELEASE NOTES

This software has been tested under Linux, MacOSX and Windows. Supported (tested)
compilers are:

	- g++ (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
	- clang++ (Apple LLVM version 5.1 (clang-503.0.40))
	- Microsoft Visual Studio 2012    

We assume the user has the compiler already installed on his machine.

## 3. COMPILING

The software can be compiled on any platform with the appropriate compiler as listed in
section 2.

MetaSim2.0 build system is based on CMake, the cross-platform, open-source build system.
To compile MetaSim2.0 you must have CMake (ver. >= 2.6) installed on your machine.

If you altready have CMake installed on your machine you can skip the
following section and jump to section 3.2.

### 3.1. Installing CMake

Follow the instructions at http://www.cmake.org/cmake/help/install.html

### 3.2. Compiling under Unix-like systems (including Mac OS X)

The steps to build and install the software are the usual ones:

    cd metasim2.0
    mkdir build
    cd build
    ccmake ..
    
The execution of "ccmake .." command cause CMake program execution.
To generate the makefile needed to compile the library, you have to press 'c' key twice
and then press 'g'. By pressing 'g' CMake will generate the makefile and will go back 
the the command line.
Now you can compile the library:

    make 

Last step will compile the library, the executable for the test and the examples included
with the library.
Output directories are:
	- src/
	- test/
	- examples/
	
The library is located in src/

### 3.3. Compiling under Windows

    execute CMake

In the location "Where is the source code:" indicate the path to the folder metasim2.0
In the location "Where to build the binaries:" indicate the path to the folder where you
want to put the output (usually = ${Path to metasim2.0}/build).
Now click "Configure". CMake will ask to specify the generator for the project. You should
select Visual Studio 11 and click Finish. When the process will finish, click again on
"Configure" and then click to "Generate".
This last step will generate the Visual Studio project "metasim.sln".
Open the folder you selected for your output and double click on the generated file 
"metasim.sln" to open the project. In Visual Studio and then in the command bar select the
BUILD menu and click Build Solution. Compilation process will start.
Output directories are:
	- src/Debug/
	- test/Debug/
	- examples/Debug/
	
The library is located in src/Debug

### 3.4. Test

Beside testing is not mandatory, we highly recommend to execute it.
The test suite is located in test/ (unix-like systems) or in /test/Debug (windows systems)
and can be executed to test if the compilation flow went ok.

#### For unix-like systems

	cd metasim2.0/build
	make
	ctest --output-on-failure

#### For Windows systems

Open the MetaSim project generated by CMake and build `ALL_BUILD`. Then,

	cd metasim2.0/build
	ctest --output-on-failure -C Debug

or

	ctest --output-on-failure -C Release

#### Results
The execution must terminate with all tests passed.

The tests have been written using the Catch library, which is a single
include file that you can find in the test directory.

https://github.com/philsquared/Catch

The testing process is automated by CTest, as an element of the CMake suite.


## 4. INSTALLING

Currently, installation is not supported. After compilation, all
header files and the library file are found in the src/ (src/Debug for Windows systems)
directory. Simply put the path of the src directory in the CPPFLAGS
and in the LDFLAGS when you want to use the library. 


## 5. RUNNING THE EXAMPLES
Every directory under one of the "examples" directories contains a
different example. Go inside the directory and run the executable
file.

### 5.1 Unix-like systems
For example, to run the eth example, go inside the directory examples/eth and type

  ./eth
  
### 5.2 Windows systems
For example, to run the eth example, go inside the directory examples/Debug/eth and double
click on eth.exe.

## 6. ADD A NEW EXAMPLE

To add a new example to the library, you have to

- Create a new folder in metasim2.0/examples with the name of your example.
- Edit the file metasim2.0/examples/CMakeLists.txt adding the specification for your
example:
	add_subdirectory(name_of_your_example)
	
Once you wrote the code of your example, you should re-generate the makefile. Follow
the instructions in section 3 for the generation of the makefile and compile.

## 7. BUGS AND CONTRIBUTIONS

For bug reports, feature requests and other issues you may encounter,
please refer to the appropriate pages on the github site:

  http://github.com/glipari/metasim2.0


Giuseppe Lipari
g.lipari@sssup.it

Fabio Cremona
f.cremona@sssup.it
