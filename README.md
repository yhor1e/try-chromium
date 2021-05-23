# try-chromium

https://chromium.googlesource.com/chromium/src/+/refs/heads/main/docs/mac_build_instructions.md

- [ ] System requirements
  - `$ ls `xcode-select -p`/Platforms/MacOSX.platform/Developer/SDKs`
- [x] Install depot_tools
  - [x] `$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git`
  - [x] `$ export PATH="$PATH:/path/to/depot_tools"`
- [ ] Get the code
  - [x] `$ git config --global core.precomposeUnicode true`
  - [x] `$ mkdir chromium && cd chromium`
  - [ ] `fetch --no-history chromium`
  - [ ] `$ cd src`
- [ ] Setting up the build
  - `$ gn gen out/Default`
- [ ] Build Chromium
  - `$ autoninja -C out/Default chrome`
- [ ] Run Chromium
  - `$ out/Default/Chromium.app/Contents/MacOS/Chromium`
