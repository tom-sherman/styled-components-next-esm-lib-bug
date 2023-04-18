# Styled Components, Microbundle, ESM Bug with Next.js

This is a minimal reproduction of a bug with styled-components and Next.js.

Next.js is importing the modern.js output from the build lib. In this module, styled-components default export doesn't seem to have the relevant properties eg. `styled.button`.

## To Reproduce

1. Clone this repo
2. `pnpm i`
3. `pnpm run --filter=./lib build`
4. `pnpm run --filter=./app dev`
5. Open localhost:3000

## Expected behaviour
Should render a red button

## Actual behaviour

There is a build error:

```
error - ../lib/dist/button.modern.js (1:47) @ eval
error - Error [TypeError]: styled_components__WEBPACK_IMPORTED_MODULE_0__.button is not a function
    at eval (webpack-internal:///../lib/dist/button.modern.js:6:62
```

Also if you run the `next build` script:

```
TypeError: external_styled_components_namespaceObject.button is not a function
    at 947 (~/styled-components-next-esm-lib-bug/app/.next/server/pages/index.js:24:58)
```
