---
layout: page
title: Blog
---
<section id="blog">
    <h2>Articles</h2>
    <p>I hope to document this journey through a series of posts here.</p>
    <br>
    <article>
      <h3 style="display: none;">All posts</h3>
    {% for post in site.posts %}
    <a href="{{ post.url }}">{{ post.title }}</a> <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%e %B, %Y" }}</time><br><span class="blurb">{{ post.blurb }}</span><br><span class="tags">{{ post.tags | sort | join: ", " }}</span><br><br>
    {% endfor %}
    </article>

  <h2>All Tags</h2>
    <p class="tags">
    {% for tag in site.tags %}
      {% assign t = tag | first %}
      <span style="padding-right:2em;">{{ t | downcase }}</span>
    {% endfor %}
    </p>
</section>
