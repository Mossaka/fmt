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

# Quick Build Check

Do a minimal build check of fmtlib/fmt.

## Instructions

1. Check available tools: `which cmake g++`

2. Find cmake if not in PATH: `find /opt -name cmake -type f 2>/dev/null | head -1`

3. Configure and build the library only (no tests):
   - `mkdir -p build && cd build && cmake .. -DFMT_TEST=OFF`
   - `make -j2 fmt`

4. Verify the library built: `ls -la build/libfmt.a`

5. Report success and exit.
