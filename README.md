<a href="https://marked.js.org">
  <img width="60px" height="60px" src="https://marked.js.org/img/logo-black.svg" align="right" />
</a>

# Marked

[![npm](https://badgen.net/npm/v/marked)](https://www.npmjs.com/package/marked)
[![gzip size](https://badgen.net/badgesize/gzip/https://cdn.jsdelivr.net/npm/marked/marked.min.js)](https://cdn.jsdelivr.net/npm/marked/marked.min.js)
[![install size](https://badgen.net/packagephobia/install/marked)](https://packagephobia.now.sh/result?p=marked)
[![downloads](https://badgen.net/npm/dt/marked)](https://www.npmjs.com/package/marked)
[![dep](https://badgen.net/david/dep/markedjs/marked?label=deps)](https://david-dm.org/markedjs/marked)
[![dev dep](https://badgen.net/david/dev/markedjs/marked?label=devDeps)](https://david-dm.org/markedjs/marked?type=dev)
[![travis](https://badgen.net/travis/markedjs/marked)](https://travis-ci.org/markedjs/marked)
[![snyk](https://snyk.io/test/npm/marked/badge.svg)](https://snyk.io/test/npm/marked)

- ⚡ built for speed
- ⬇️ low-level compiler for parsing markdown without caching or blocking for long periods of time
- ⚖️ light-weight while implementing all markdown features from the supported flavors & specifications
- 🌐 works in a browser, on a server, or from a command line interface (CLI)

## Forked Changes

### Support image size configuration

#### simple width and height

{number}x{number} in the title text part of the link in quotes after the url e.g.

```md
![](src "1x2 title text")
or
![](src "title text 1x2")
```

generates:
```html
<img src="src" alt="" width="1" height="2" title="title text">
```

#### explicit attributes

any attribute name=value, no quotes around the value e.g.

```md
![](src "width=1 height=2 align=right title text")
![](src "width=1px height=2px align=right title text")
```

generates:
```html
<img src="src" alt="" width="1" height="2" align="right" title="title text">
<img src="src" alt="" width="1px" height="2px" align="right" title="title text">
```

### baseUrl works on html tag

The original code doesn't apply the `baseUrl` on the relative link in raw html tag such as `<a href="">`, `<img src="">`.

Hack the render function, this will add `baseUrl` just as it dose on markdown image, `![](path/to/image.png)`.

## Demo

Checkout the [demo page](https://marked.js.org/demo/) to see marked in action ⛹️

## Docs

Our [documentation pages](https://marked.js.org) are also rendered using marked 💯

Also read about:

* [Options](https://marked.js.org/#/USING_ADVANCED.md)
* [Extensibility](https://marked.js.org/#/USING_PRO.md)

## Installation

**CLI:** `npm install -g marked`

**In-browser:** `npm install marked`

## Usage

### Warning: 🚨 Marked does not [sanitize](https://marked.js.org/#/USING_ADVANCED.md#options) the output HTML by default 🚨

**CLI**

``` bash
$ marked -o hello.html
hello world
^D
$ cat hello.html
<p>hello world</p>
```

**Browser**

```html
<!doctype html>
<html>
<head>
  <meta charset="utf-8"/>
  <title>Marked in the browser</title>
</head>
<body>
  <div id="content"></div>
  <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
  <script>
    document.getElementById('content').innerHTML =
      marked('# Marked in the browser\n\nRendered by **marked**.');
  </script>
</body>
</html>
```

## License

Copyright (c) 2011-2018, Christopher Jeffrey. (MIT License)
