This is an example project of how to use threads in C++ with WebAssembly and how
to communicate between the C++ and JavaScript worlds with Embind.

# Setup

* Install cmake.
* Install and initialize the Emscripten SDK from https://emscripten.org.
* Then:
```
mandelbrot-wasm # mkdir build
mandelbrot-wasm # cd build
mandelbrot-wasm # emcmake cmake ..
mandelbrot-wasm # make
mandelbrot-wasm # emrun --port 8000 --no_browser .
```
* Point your browser to http://localhost:8000/www/index.html

# Important note to mobile users:

Unfortunately. mobile browsers currently do not support running multi-threaded WebAssembly. Sorry!

# Important note to Chrome/Chromium users:

Chrome/Chromium 68 or higher is required.

https://www.chromium.org/Home/chromium-security/ssca

# Important note to Edge users:

Edge 79 or higher is required.

https://blogs.windows.com/msedgedev/2018/01/03/speculative-execution-mitigations-microsoft-edge-internet-explorer/

# Important note to Firefox users:

**TL;DR:** It won't run in Firefox right now. Mozilla is working to fix it (since 2018...).

Due to several security enforcements, Firefox is currently (Firefox 77) still unable
to run multi-threaded WebAssembly.

* Because of the Spectre vulnerability, Firefox (temporarily?) disabled support
  for `SharedArrayBuffer` in 2018. This effectively disables the use of
  multi-threaded WebAssembly.

  https://blog.mozilla.org/security/2018/01/03/mitigations-landing-new-class-timing-attack/

  It can be enabled (with the risk of Spectre vulnerability) in `about:config`:
  ```
  javascript.options.shared_memory = true
  ```
  Enable at your own risk.

* Further enforcement are in place, too, making life hard.

  https://github.com/emscripten-core/emscripten/issues/10014

* You might have a better chance of running this code in Firefox Nightly.

  * https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SharedArrayBuffer/Planned_changes

  * https://bugzilla.mozilla.org/show_bug.cgi?id=1619649
