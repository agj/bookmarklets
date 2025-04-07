# Bookmarklets

These are some [bookmarklets](wiki-bookmarklet) I've written for myself. Drag the links into your bookmarks to save, and press it to activate it.

[wiki-bookmarklet]: https://en.wikipedia.org/wiki/Bookmarklet

## Elm Debug Transformer

Useful for [Elm](https://elm-lang.org/) programmers. Enables (Elm Debug Transformer)[https://github.com/kraklin/elm-debug-transformer] in the current page, which improves the console logging output to make it more readable.

**Bookmarklet:**

- [Elm Debug Transformer][elm-debug-transformer] (version: 1.2.1)

The code:

```js
console.info("Loading Elm Debug Transformer…");
import("//unpkg.com/elm-debug-transformer@1.2.1/dist/index.mjs").then(
  (ElmDebugger) => {
    ElmDebugger.register();
    console.info("Elm Debug Transformer loaded!");
  },
);
```

[elm-debug-transformer]: javascript:(function()%7Bconsole.info(%22Loading%20Elm%20Debug%20Transformer%E2%80%A6%22)%3B%0Aimport(%22%2F%2Funpkg.com%2Felm-debug-transformer%401.2.1%2Fdist%2Findex.mjs%22).then(%0A%20%20(ElmDebugger)%20%3D%3E%20%7B%0A%20%20%20%20ElmDebugger.register()%3B%0A%20%20%20%20console.info(%22Elm%20Debug%20Transformer%20loaded!%22)%3B%0A%20%20%7D%2C%0A)%3B%7D)()%3B
