---
title: Permalinks
date: 2021-01-03
---
# Permalinks

By default, the path to each page in your site is determined by its path on the filesystem.
A file at `<project dir>/a/b/c/file.md` will create a page at `/a/b/c/file/index.html`.

For pagination, the first site page is generated at the same `/a/b/c/file/index.html` path, 
and all subsequent pages will be at the `/a/b/c/file/1/index.html`, `/a/b/c/file/2/index.html`, etc.

## Changing Permalinks

To change a permalink, add the `permalink` attribute to the page's data:

``` markdown
<!-- <project dir>/a/b/c/file.md -->

---

permalink: /x/y/z/

---

# Hello
```

This page will be found at `/x/y/z/index.html` in your site folder.

You can also optionally specify the extension, e.g. `permalink: /x/y/z/index.css`

## Templates in Permalinks

You can also generate your permalink from a template:

``` markdown
<!-- <project dir>/a/b/c/file.md -->

---

permalink: /{{ data.newpath }}/

---
```