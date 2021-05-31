# try-chromium

https://chromium.googlesource.com/chromium/src/+/refs/heads/main/docs/mac_build_instructions.md

## Build

- [x] System requirements
  - `$ ls `xcode-select -p`/Platforms/MacOSX.platform/Developer/SDKs`
- [x] Install depot_tools
  - [x] `$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git`
  - [x] `$ export PATH="$PATH:/path/to/depot_tools"`
- [x] Get the code
  - [x] `$ git config --global core.precomposeUnicode true`
  - [x] `$ mkdir chromium && cd chromium`
  - [ ] `$ fetch --no-history chromium`
    - [x] `$ gclient sync` https://github.com/yhor1e/try-chromium/issues/1
  - [x] `$ cd src`
- [x] Setting up the build
  - `$ gn gen out/Default`
- [x] Build Chromium
  - `$ autoninja -C out/Default chrome`
- [x] Run Chromium
  - `$ out/Default/Chromium.app/Contents/MacOS/Chromium`

# Debug

- [x] Usage of tools/lldb/lldbinit.py
  - https://chromium.googlesource.com/chromium/src/+/main/docs/lldbinit.md
  - [x] To use, add the following to your ~/.lldbinit
    ``` 
    # So that lldbinit.py takes precedence.
    script sys.path[:0] = ['<.../path/to/chromium/src/tools/lldb>']
    script import lldbinit
    ```
  - [x] `$ lldb out/Default/Chromium.app/Contents/MacOS/Chromium`
