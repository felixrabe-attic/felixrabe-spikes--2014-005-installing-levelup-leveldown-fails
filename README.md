# npm install levelup leveldown - installs incompatible versions

rvagg/node-levelup#282

## tl;dr

    npm install levelup leveldown

currently results in

    LevelUPError: Installed version of LevelDOWN (1.0.0) does not match required version (~0.10.0)

## Full example

```
$ mkdir example

$ cd example

$ npm install levelup leveldown
...
levelup@0.19.0 node_modules/levelup
├── xtend@3.0.0
├── prr@0.0.0
├── errno@0.1.1
├── bl@0.8.2
├── semver@2.3.2
├── readable-stream@1.0.31 (isarray@0.0.1, inherits@2.0.1, string_decoder@0.10.31, core-util-is@1.0.1)
└── deferred-leveldown@0.2.0 (abstract-leveldown@0.12.4)

leveldown@1.0.0 node_modules/leveldown
├── bindings@1.2.1
├── fast-future@1.0.1
├── nan@1.3.0
└── abstract-leveldown@2.0.1 (xtend@3.0.0)

$ cat > example.js
var levelup = require('levelup');
var db = levelup('example.db');

$ node example.js

/.../example/node_modules/levelup/lib/util.js:59
    throw new LevelUPError(
          ^
LevelUPError: Installed version of LevelDOWN (1.0.0) does not match required version (~0.10.0)
    at getLevelDOWN (/.../example/node_modules/levelup/lib/util.js:59:11)
    at LevelUP.open (/.../example/node_modules/levelup/lib/levelup.js:113:37)
    at new LevelUP (/.../example/node_modules/levelup/lib/levelup.js:86:8)
    at LevelUP (/.../example/node_modules/levelup/lib/levelup.js:46:12)
    at Object.<anonymous> (/.../example/example.js:2:10)
    at Module._compile (module.js:456:26)
    at Object.Module._extensions..js (module.js:474:10)
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Function.Module.runMain (module.js:497:10)
```
