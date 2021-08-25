---
title: Command-line Usage
---

# Command-line Usage

## To run Skip 

``` bash
skip
```

## To watch files in the directory and rebuild the project on changes

``` bash
skip --watch
```

## To watch and serve the site

``` bash
skip --serve
```

You can also change the port the site is served on:

``` bash
skip --serve --port 9090
```

default is **8080**

## To change the directory the site is output to

``` bash
skip --output _mysite
```

default is **_site**

## To copy files into the site folder

``` bash
skip --copy style.css
```

This also works for multiple files

``` bash
skip --copy style.css robots.txt
```

To change the location a file is copied to, add a `:` followed by the location within the _site folder:

``` bash
skip --copy style.css:css/style.css
```

The resulting file will be at `_site/css/style.css`.

This will also recursively copy directories

``` bash
skip --copy img
```

The `img` folder and everything it contains will be copied to the `_site` directory.

## To fail when reading from a data file produces an error

``` bash
skip --fail-on-error
```

By default Skip ignores data files that cause an error when it tries to read the data from them.
When you set this flag, the error will be raised and the build will fail.
