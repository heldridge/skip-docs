---
title: Pagination
date: "2021-01-06"
---

# Pagination

Our dog links page is great, but what if we had hundreds or thousands of dogs in our database?
In that case we would want to paginate the links over several pages.
Luckily, Skip provides a way to do this!

Change `dog-links.j2` to the following:

``` jinja2
<!-- dog-links.j2 -->
---

pagination:
    data: dogs
    size: 2

---

<ul>
    {% for dog_page in items %}
    <li>
        <a href="{{ dog_page.get_permalink() }}">
            {{ dog_page.data.name }}
        </a>
    </li>
    {% endfor %}
</ul>
```

When you specify the special `pagination` attribute Skip will create multiple pages, looping over the items you choose in the `data` sub-attribute in chunks of `size`.

In our case this will generate two files, `dog-links/index.html` and `dog-links/1/index.html`.
If we had more dogs, link pages would be generated at `dog-links/2/index.html`, `dog-links/3/index.html`, etc.

If we wanted to add a link to the next page of dog links, we could use the special `index` attribute.
All pagination pages have an `index` attribute that represents which pagination chunk is currently being processed:

``` jinja2
<!-- dog-links.j2 -->
---

pagination:
    data: dogs
    size: 2

---

<ul>
    {% for dog_page in items %}
    <li>
        <a href="{{ dog_page.get_permalink() }}">
            {{ dog_page.data.name }}
        </a>
    </li>
    {% endfor %}
</ul>

{% if index < (collections.dogs|length)/2 - 1 %}
<a href="/dog-links/{{ index + 1}}/">Next page</a>
{% endif %}
```

We use the `if` statement to ensure that we don't get a "Next Page" link on the final page.

And that's it!
We have gone over the core concepts of Skip: project structure, layouts, data, collections, and pagination.
If you want to know more, check out the [advanced topics](/advanced/command-line-usage/).
