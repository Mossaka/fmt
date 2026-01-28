---
name: Build and Test
on:
  push:
    branches: [main, master]
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
network:
  allowed:
    - defaults
    - node
    - github
tools:
  bash:
    - "*"
  edit:
timeout-minutes: 15
---

# Build and Test fmtlib/fmt

Build and test the fmt C++ formatting library using CMake.

## Instructions

1. Check the C++ compiler and CMake version:
   - Run `g++ --version` or `clang++ --version`
   - Run `cmake --version`

2. Create a build directory and configure the project:
   - `mkdir -p build && cd build`
   - `cmake .. -DFMT_TEST=ON`

3. Build the project:
   - `cmake --build . --parallel`

4. Run the test suite:
   - `ctest --output-on-failure`

5. Report the build and test results:
   - Number of tests run
   - Number passed/failed
   - Any build warnings or errors
