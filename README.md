# How to compile our optimized ZSim and reproduce our tests

### The default version of ZSim we use is Ziqi Wang's zsim-base: https://github.com/wangziqi2013/zsim-base.
### The modified version containing our optimization implementation based on zsim-base is here: https://github.com/why1998101/zsim-optimized.
 \
To compile our optimized ZSim and reproduce our tests: 
1. Set up a fresh Ubuntu 16.04 VM using a 64-bit image, the one we use is 64-bit PC (AMD64) desktop image at: https://releases.ubuntu.com/16.04/.
2. Install build-essential, g++, git, scons.
3. Install libconfig, libhdf5, libelfg0. Note that those packages may not have the ones with the exact same names available. If so, search about this online and install an equivalent package such as libelfg0-dev.
4. Clone our [zsim-optimized](https://github.com/why1998101/zsim-optimized) directly. Then, clone this repository. \
Or, \
Clone [zsim-base](https://github.com/wangziqi2013/zsim-base). Then, clone this repository. Replace __src/coherence_ctrls.h__ and __src/coherence_ctrls.cpp__ in zsim-base with our versions in __ZSim/source_code_modified__ directory of this repository. 
Then, copy all files inside in __ZSim/test_configuration_added__ directory of this repository to the __test__ directory in zsim-base.
5. Run __make__ inside __micro_benchmarks__ directory of this repository. Copy the six executables to __misc/micro__ directory in zsim-optimized or zsim-base (zsim-base does not have this folder yet, you need to first create it).
6. Download pin-2.14 [here](https://github.com/wangziqi2013/wangziqi2013.github.io/blob/master/static/pin-2.14.tar.gz?raw=true%5D). Unpack the zip file. 
Copy the unpacked folder to root directory of zsim-optimized or zsim-base.
7. In root directory of zsim-optimized or zsim-base, run __make zsim__ to compile ZSim.
8. In root directory of zsim-optimized or zsim-base, run __./build/opt/zsim ./test/[path_to_test_configuration_file]__ to start a simulation.

Note that in step 4, whether you clone zsim-optimized or zsim-base, the instructions make it our optimized version (for zsim-base, just replace the source code we modified and add our new test configuration files to make it the same as zsim-optimized).

If you also want to compile a default version of ZSim, just clone zsim-base and run __make zsim__ if you have set up the Ubuntu 16.04 environment and installed all the required packages. If you want to run our tests using default ZSim, just copy the test executables and test configuration files to the same places (both before or after compilation is fine)
as mentioned above and start a simulation in the same way.
