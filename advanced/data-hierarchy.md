---
title: Data Hierarchy
---
# Data Hierarchy

Data for use in templates can come from the following places:

- Data files in the top-level `data` folder
- Data files nested in sub-directories
- Data in frontmatter

Data from lower down in the list overrides data from higher up.
Any nested data file overrides those from parent directories.


## Example

your project structure looks like this:

``` txt
data/
    global-data.json
posts/
    posts-data.py
    nested-dir/
        nested-data.json
        dogs.md
```

And contains the following files:

``` python
# data/global-data.json

{ "country": "United States", "color": "blue"}
```

``` python
# posts/posts-data.py

def get_data():
    return {"color": "red", "language": "English"}
```

``` python
# posts/nested-dir/nested-data.json

{ "language": "Spanish", "shape": "circle" }
```

``` jinja2
<!-- jinja2.j2 -->
---
shape: rectangle
---

<ul>
    <li> {{ data.country }} </li>
    <li> {{ data.color }} </li>
    <li> {{ data.language }} </li>
    <li> {{ data.shape }} </li>
</ul>

```

The resulting file would look like:

``` html
<ul>
    <li> United States </li>
    <li> red </li>
    <li> Spanish </li>
    <li> rectangle </li>
</ul>
```

## Data files that don't return dicts

If you have a data file that doesn't return a dict:

``` python
# data/dwarfs.py

def get_data():
    return ['Doc', 'Grumpy', 'Happy', 'Sleepy', 'Bashful', 'Sneezy', 'Dopy']
```

You access it in a template at `data.<filename>`:

``` jinja2
<ul>
    {% for dwarf in data.dwarfs %}
    <li> {{ dwarf }} </li>
    {% endfor %}
</ul>
```