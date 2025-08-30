## How to Compile on Windows

Apply the following commands in PowerShell under the directory of application

1. Create the vcpkg.json
```
vcpkg new --application
```
2. Copy the vcpkg.json
```
copy .\scripts\vcpkg.json .\vcpkg.json
```
3. Install the required libraries and dependencies using vcpkg will create vcpkg_installed directory 
```
vcpkg install --x-manifest-root=. 
```
4. Make sure the VCPKG_ROOT identified and added to envirmonet of PATH 
```
$env:VCPKG_ROOT = "C:\path\to\vcpkg"
$env:PATH = "$env:VCPKG_ROOT;$env:PATH"
```
5. Configure the CMake to use vcpkg as toolchain
```
cmake -B . -S . -D CMAKE_TOOLCHAIN_FILE="$env:VCPKG_ROOT/scripts/buildsystems/vcpkg.cmake" 
```
6. Build the using CMake for release mode use --config Release
```
cmake --build . <--config Release>
```
