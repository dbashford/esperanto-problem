esperanto-problem
=================

Repo to illustrate issue with esperanto CLI.

Run `esperanto -b -i htmlbars-runtime.js -o htmlbars-runtime-bundle.js --strict`

Look in `runtime-bundle` file.  At bottom note the following lines of code:
```javascript
__export('hooks', function () { return htmlbars_runtime__hooks; });
__export('helpers', function () { return htmlbars_runtime__helpers; });
__export('Morph', function () { return htmlbars_runtime__Morph; });
__export('DOMHelper', function () { return htmlbars_runtime__DOMHelper; });
```

All of the values following the returns (`htmlbars_runtime__hooks`, etc) do not exist.

Changing those 4 lines to these 4 lines nets the desired result:
```javascript
__export('hooks', function () { return hooks__default; });
__export('helpers', function () { return helpers__default; });
__export('Morph', function () { return Morph__default; });
__export('DOMHelper', function () { return DOMHelper__default; });
```
