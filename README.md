## slsDetectorTango



### slsDetectorPackage

Install the [required dependencies](https://slsdetectorgroup.github.io/devdoc/dependencies.html) of slsDetectorPackage libraries and build the package from [sources](https://github.com/slsdetectorgroup/slsDetectorPackage):

```bash
# clone the library
curl -L https://github.com/slsdetectorgroup/slsDetectorPackage/archive/refs/tags/10.0.0.tar.gz > slsDetectorPackage.tar.gz
tar -xzf slsDetectorPackage.tar.gz && cd slsDetectorPackage-10.0.0
cmake -B build -DSLS_DEVEL_HEADERS=ON -DSLS_BUILD_SHARED_LIBRARIES=ON
# build the library
cmake --build build -j
# install the library (requires write access to /usr/lib etc)
sudo cmake --install build
```
