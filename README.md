# Bookmarklets

These are some [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet) I've written for myself. To use, copy the bookmarklet code, create a new bookmark in your browser, and paste it as the URL. Then you can just press it to activate it.

## Elm Debug Transformer

Useful for [Elm](https://elm-lang.org/) programmers. Enables [Elm Debug Transformer](https://github.com/kraklin/elm-debug-transformer) in the current page, which improves the console logging output to make it more readable.

Bookmarklet (version: 1.2.1):

```js
javascript:(function()%7Bconsole.info(%22Loading%20Elm%20Debug%20Transformer%E2%80%A6%22)%3B%0Aimport(%22%2F%2Funpkg.com%2Felm-debug-transformer%401.2.1%2Fdist%2Findex.mjs%22).then(%0A%20%20(ElmDebugger)%20%3D%3E%20%7B%0A%20%20%20%20ElmDebugger.register()%3B%0A%20%20%20%20console.info(%22Elm%20Debug%20Transformer%20loaded!%22)%3B%0A%20%20%7D%2C%0A)%3B%7D)()%3B
```

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

## Save URL to Obsidian

A very basic way to help you use [Obsidian](https://obsidian.md/) as your web bookmarks manager. Creates a new note using the current page's title as the note's title, and puts the URL in the body. If you select some text on the page, it will get copied and quoted in the note as well.

Based on [this](https://forum.obsidian.md/t/bookmarklet-send-to-obsidian/13415). Also, for a more complex/complete solution, [see here](https://stephango.com/obsidian-web-clipper).

Bookmarklet:

```js
javascript:(function()%7Bconst%20title%20%3D%20document.title.replaceAll(%2F%3A%2Fg%2C%20%22%22)%3B%0Aconst%20url%20%3D%20document.location.href%3B%0Aconst%20selection%20%3D%20window.getSelection().toString().trim()%3B%0Aconst%20quote%20%3D%0A%20%20selection%20!%3D%3D%20%22%22%0A%20%20%20%20%3F%20selection%0A%20%20%20%20%20%20%20%20.split(%22%5Cn%22)%0A%20%20%20%20%20%20%20%20.map((line)%20%3D%3E%20%60%3E%20%24%7Bline%7D%60)%0A%20%20%20%20%20%20%20%20.join(%22%5Cn%22)%0A%20%20%20%20%3A%20%22%22%3B%0A%0Aconst%20content%20%3D%20%60%24%7Burl%7D%0A%0A%24%7Bquote%7D%0A%60%3B%0A%0Adocument.location.href%20%3D%20%60obsidian%3A%2F%2Fnew%3Fname%3D%24%7BencodeURIComponent(title)%7D%26content%3D%24%7BencodeURIComponent(content)%7D%60%3B%7D)()%3B
```

The code:

```js
const title = document.title.replaceAll(/:/g, "");
const url = document.location.href;
const selection = window.getSelection().toString().trim();
const quote =
  selection !== ""
    ? selection
        .split("\n")
        .map((line) => `> ${line}`)
        .join("\n")
    : "";

const content = `${url}

${quote}
`;

document.location.href = `obsidian://new?name=${encodeURIComponent(title)}&content=${encodeURIComponent(content)}`;
```

## Open Instagram image

Opens the current post's image in the current tab.

Bookmarklet:

```
javascript:void%20function(){const%20a=document.querySelector(%22section%20main%20img%22)%3F.getAttribute(%22src%22);a%3Fwindow.location=a:console.error(%22Failed%20to%20get%20image%20URL.%22)}();
```

The code:

```js
const url = document.querySelector("section main img")?.getAttribute("src");
if (url) {
  window.location = url;
} else {
  console.error("Failed to get image URL.");
}
```
