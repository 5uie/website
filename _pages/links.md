---
layout: page
title: Bookmarks
permalink: /bookmarks.html
---

<article>
Reverse chronological list of interesting links on the web (this is an
attempt to replace or recreate del.icio.us),
<br><br><br>

{% if site.data.bookmarks %}
{% for link in site.data.bookmarks %}
<a href="{{ link.url }}">{{ link.title }}</a><br><span
class="tags">Tags: {{ link.tags }}</span><br>Last accessed date:<time datetime="{{ link.date | date_to_xmlschema }}">{{ link.date | date: "%e %B, %Y" }}</time><br><br>
{% endfor %}
{% endif %}
</article>
