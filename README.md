# flow-typed install bug

Instructions:

1. Clone this repo.
2. Run `npm install`.
3. Run `npm test`.
4. Run `git diff`.

Expected: No diff.

Actual: The react-router-dom definition has been updated.

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


$ git diff
diff --git a/flow-typed/npm/react-router-dom_v4.x.x.js b/flow-typed/npm/react-router-dom_v4.x.x.js
index f112ec7..93b4f53 100644
--- a/flow-typed/npm/react-router-dom_v4.x.x.js
+++ b/flow-typed/npm/react-router-dom_v4.x.x.js
@@ -1,5 +1,5 @@
-// flow-typed signature: 493d39fe9968f54f645635dbec3b2d9a
-// flow-typed version: 02d9734356/react-router-dom_v4.x.x/flow_>=v0.38.x
+// flow-typed signature: a52ef25660e2172052618e087e7f31b7
+// flow-typed version: 37d8964a70/react-router-dom_v4.x.x/flow_>=v0.38.x <=v0.52.x
 
 declare module 'react-router-dom' {
   declare export class BrowserRouter extends React$Component {
@@ -161,9 +161,11 @@ declare module 'react-router-dom' {
   declare export function withRouter<P, S>(Component: ClassComponent<void, P, S> | FunctionComponent<P>): ClassComponent<void, $Diff<P, ContextRouter>, S>;
 
   declare type MatchPathOptions = {
-    path: string,
+    path: ?string,
     exact?: boolean,
     strict?: boolean,
-  }
-  declare export function matchPath(pathname: string, options: MatchPathOptions): null | Match
+    sensitive?: boolean
+  };
+
+  declare export function matchPath(pathname: string, options?: MatchPathOptions | string): null | Match
 }
```
