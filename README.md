# Napi Thread-Safe Callback

This package contains a header-only C++ helper class to facilitate
calling back into JavaScript from threads other than the Node.JS main thread

## Usage

  1. Add a dependency on this package to `package.json`:
```json
  "dependencies": {
    "napi-thread-safe-callback": "0.0.1",
  }
```

  2. Reference this package's include directory in `binding.gyp`:
```gyp
  'include_dirs': ["<!@(node -p \"require('napi-thread-safe-callback').include\")"],
```
  3. Include the header in your code:
```C++
#include "napi-thread-safe-callback.hpp"
```

  4. Use the class - TODO

### Exception handling

Exceptions need to be enabled in the native module. To do this use the following
in `binding.gyp`:
```gyp
  'cflags!': [ '-fno-exceptions' ],
  'cflags_cc!': [ '-fno-exceptions' ],
  'xcode_settings': {
    'GCC_ENABLE_CPP_EXCEPTIONS': 'YES',
    'CLANG_CXX_LIBRARY': 'libc++',
    'MACOSX_DEPLOYMENT_TARGET': '10.7',
  },
  'msvs_settings': {
    'VCCLCompilerTool': { 'ExceptionHandling': 1 },
  },
  'conditions': [
    ['OS=="win"', { 'defines': [ '_HAS_EXCEPTIONS=1' ] }]
  ]
```
