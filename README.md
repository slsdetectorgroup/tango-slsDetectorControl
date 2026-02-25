## slsDetectorTango



### slsDetectorPackage

Install the [required dependencies](https://slsdetectorgroup.github.io/devdoc/dependencies.html) of slsDetectorPackage libraries and build the package from [sources](https://github.com/slsdetectorgroup/slsDetectorPackage):

```bash
# clone the library
git clone --depth 1 --branch X.X.X \
https://github.com/slsdetectorgroup/slsDetectorPackage.git
cd slsDetectorPackage
cmake -B build -DSLS_DEVEL_HEADERS=ON -DSLS_BUILD_SHARED_LIBRARIES=ON
# build the library
cmake --build build -j
# install the library (requires write access to /usr/lib etc)
sudo cmake --install build
```
