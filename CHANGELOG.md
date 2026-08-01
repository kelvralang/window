# Changelog

## 0.1.6

- Correct the minimum supported runtime to Mog 0.1.4, the first release that
  embeds its configured package-compatibility version correctly.
- Add pinned multi-target CI/release automation with tag checks, runtime tests,
  checksummed native archives, and automated action updates.
- Remove C++20-only constant initialization from the C++17 native build.
- Correct the supported target list published by the v0.1.5 manifest.
- Add window and event IDs so events from SDL's process-wide queue can be routed
  correctly in multi-window programs.
- Report mouse coordinates relative to the requested window.
- Exercise window lifecycle and drawing APIs in the package smoke test.
- Correct package metadata to match the repository's GPL-3.0-only license text.

## 0.1.5

- Package the macOS native module using CMake's `.so` output under Mog's required `.dylib` artifact name.

## 0.1.4

- Fix GitHub Release artifact packaging for Linux and macOS builds.

## 0.1.3

- Require Mog runtime 0.1.1 or newer for local native package loading.

## 0.1.2

- Add package constants and SDL2-backed window, input, drawing, and timing APIs.
