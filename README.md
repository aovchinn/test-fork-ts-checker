# test-fork-ts-checker
created as a showcase for: https://github.com/TypeStrong/fork-ts-checker-webpack-plugin/issues/557

* cd my-shared-stuff
* npm link
* cd ../app
* npm i
* npm link my-shared-stuff
* npm run watch
* fix ts errors in my-shared-stuff/index.ts 

## result
```
Type-checking in progress...
ERROR in ./node_modules/my-shared-stuff/index.ts 2:1-2
TS2322: Type 'string' is not assignable to type 'number'.
    1 | let a = 1;
  > 2 | a = "asd";
      | ^
    3 | export { a };
    4 |
    5 | let b = 1;

ERROR in ./node_modules/my-shared-stuff/index.ts 6:1-2
TS2322: Type 'string' is not assignable to type 'number'.
    4 |
    5 | let b = 1;
  > 6 | b = "bsd";
      | ^
    7 | export { b };

Found 2 errors in 2271 ms.
```
after commenting b assignment
```
asset main.js 3.79 KiB [emitted] (name: main)
cached modules 1.06 KiB [cached] 1 module
../my-shared-stuff/index.ts 192 bytes [built] [code generated]
webpack 5.68.0 compiled successfully in 62 ms
ERROR in ./node_modules/my-shared-stuff/index.ts 2:1-2
TS2322: Type 'string' is not assignable to type 'number'.
    1 | let a = 1;
  > 2 | a = "asd";
      | ^
    3 | export { a };
    4 |
    5 | let b = 1;

ERROR in ./node_modules/my-shared-stuff/index.ts 6:1-2
TS2322: Type 'string' is not assignable to type 'number'.
    4 |
    5 | let b = 1;
  > 6 | // b = "bsd";
      | ^
    7 | export { b };

Found 2 errors in 103 ms.
```