# Kelvra Window

`github.com/kelvralang/window` is Kelvra's SDL2-backed native window, input, and
immediate-mode drawing package. Version 0.2.0 supports Linux x86_64/ARM64 and
macOS ARM64 with native ABI 3 and Kelvra `^0.2.0`.

## Install and import

Git installs are built from source, so users need Git, CMake, a C++17 compiler,
and SDL2 development files:

```bash
kelvra add github.com/kelvralang/window@v0.2.0
```

```kelvra
const window = @import("github.com/kelvralang/window")

var win window.Window = window.create("Demo", 800, 600)
window.show(win)
window.clearRgb(win, 32, 64, 96)
window.fillRect(win, 20, 20, 120, 80, 255, 180, 0)
window.drawText(win, 24, 32, "Hello, Kelvra", 2, 255, 255, 255)
window.present(win)
window.delay(1000)
window.close(win)
```

The canonical module path is recommended in shared code. The `window` alias is
also available to projects whose installed package metadata declares it.

## Events and multiple windows

SDL owns one process-wide event queue. `pollEvent(win)` validates that `win` is
open and returns the next process event; it does not filter the queue. Compare
`eventWindowId(event)` with `windowId(win)` when a program owns multiple windows.
Process-wide events such as `quit` report window ID `0`.

Supported event kind strings currently include `quit`, `key_down`, `key_up`,
`mouse_move`, `mouse_down`, and `mouse_up`; other SDL events report `unknown`.
Mouse coordinates are returned relative to the window passed to `mouseX` or
`mouseY`.

## Native artifacts

GitHub Releases contain convenience native archives for targets built by the
release workflow. Kelvra Git dependencies do not consume those archives: they build
this repository from source. Prebuilt installation requires publishing the
artifact through a configured Kelvra registry with `kelvra publish`.

Build directly with:

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```

The complete public contract is in `package.api.kel`. The package is licensed
under GPL-3.0-only; see `LICENSE`.
