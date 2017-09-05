# flow-typed install bug

Instructions:

1. Clone this repo.
2. Run `npm install`.
3. Run `npm test` twice.

```
$ npm test

> @ test /home/lydell/bugs/flow-typed
> flow-typed install --ignoreDeps dev

• Found 1 dependencies in package.json to install libdefs for. Searching...
• rebasing flow-typed cache...
• Installing 1 libDefs...
  • react-router-dom_v4.x.x.js
    └> ./flow-typed/npm/react-router-dom_v4.x.x.js
react-router-dom
/home/lydell/bugs/flow-typed/flow-typed/npm
• The following installed libdefs are compatible with your dependencies, but may not include all minor and patch changes for your specific dependency version:

  • libdef: react-router-dom_v4.x.x (satisfies react-router-dom@^4.2.2)

  Consider submitting a versioned update for this package to 
  https://github.com/flowtype/flow-typed/


$ npm test

> @ test /home/lydell/bugs/flow-typed
> flow-typed install --ignoreDeps dev

• Found 1 dependencies in package.json to install libdefs for. Searching...
UNCAUGHT ERROR: Error: flow_v0.38.x <=v0.52.x: Unexpected trailing characters:  <=v0.52.x
    at validationError (/home/lydell/bugs/flow-typed/node_modules/flow-typed/dist/lib/validationErrors.js:14:11)
    at parseDirString (/home/lydell/bugs/flow-typed/node_modules/flow-typed/dist/lib/flowVersion.js:155:45)
    at _callee2$ (/home/lydell/bugs/flow-typed/node_modules/flow-typed/dist/lib/npm/npmLibDefs.js:543:146)
    at tryCatch (/home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:65:40)
    at Generator.invoke [as _invoke] (/home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:303:22)
    at Generator.prototype.(anonymous function) [as next] (/home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:117:21)
    at tryCatch (/home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:65:40)
    at invoke (/home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:155:20)
    at /home/lydell/bugs/flow-typed/node_modules/regenerator-runtime/runtime.js:165:13
    at <anonymous>
```
