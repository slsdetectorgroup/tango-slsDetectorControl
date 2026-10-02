## tango-slsDetectorControl
[![build on ubuntu](https://github.com/slsdetectorgroup/tango-slsDetectorControl/actions/workflows/build-and-test.yml/badge.svg)](https://github.com/slsdetectorgroup/tango-slsDetectorControl/actions/workflows/build-and-test.yml)

Tango Device Server for control of PSI detectors.

## Features
This software implements read/write access to the most of the detector parameters.

This project aims to offer a universal single TangoDS for all of the PSI detectors based on the Tango dynamic attributes.

An instance of `slsReceiver` can be automatically started alongside the TangoDS (specify the `ReceiverExecutablePath`, `ReceiverPort` and `StartReceiverOnStartup` properties if necessary).

## Dependecies
### cppTango
Follow the platform dependent [official installation guide](https://tango-controls.readthedocs.io/en/latest/How-To/installation/index.html) of Tango Controls.

### slsDetectorPackage
Follow the [official installation guide](https://slsdetectorgroup.github.io/slsDetectorPackage/10.0.0/installation.html) of slsDetectorPackage to install the necessary dependecies.

Supported are slsDetectorPackage versions non less than 8.
For the 
```bash
# clone the library
curl -L https://github.com/slsdetectorgroup/slsDetectorPackage/archive/refs/tags/X.X.X.tar.gz > slsDetectorPackage.tar.gz
tar -xzf slsDetectorPackage.tar.gz && cd slsDetectorPackage-X.X.X
# ensure that both developer headers and shared libraries are enabled
cmake -B build -DSLS_DEVEL_HEADERS=ON -DSLS_BUILD_SHARED_LIBRARIES=ON -DCMAKE_INSTALL_PREFIX=...
# build the library
cmake --build build -j
# install the library
cmake --install build
```

## Installation
```bash
git clone https://github.com/slsdetectorgroup/tango-slsDetectorControl.git && cd tango-slsDetectorControl
# embed the slsReceiver instance in the TangoDS execetuable if needed
cmake -B build -DSLS_DET_EMBED_RECEIVER=OFF

cmake --build build -j
cmake --install build
```

## Help
* [slsDetectorPackage detector API](https://slsdetectorgroup.github.io/slsDetectorPackage/10.0.0/detector.html)
* [Tango Controls reference](http://tango-controls.readthedocs.io/en/latest/Reference/index.html)
