---
layout: page
title: About
---

<h2>Co-ordinates:</h2>

{% if site.data.smprofiles %}
{% assign sm = site.data.smprofiles %}
{% for entry in sm %}
{% assign key = entry | first %}
{% if sm[key].id %}
- {{ sm[key].title }}: <a href="{{ sm[key].href }}" title="{{ sm[key].title }}">{{ sm[key].id }}</a>
{% endif %}
{% endfor %}
{% endif %}

Signed emails are preferred, and here is my [public key](/publickey.txt).

<br >
<h2>Site details:</h2>

- Feed: [Atom Feed](/feed.xml)
- Sitemap: [XML](/sitamap.xml)
- Source: [GitHub](https://github.com/5uie/website)

<br >
<h2>Colophon:</h2>

This site has been [validated](https://validator.w3.org/nu/?doc=https://5uie1.netlify.app) to be HTML5 safe. Please see why it is important to validate [here](https://validator.w3.org/docs/why.html), [here](https://universaldesign.ie/technology-ict/web-accessibility-techniques1/developer-s-introduction-and-index/dev-7-–-code-according-to-best-practices/dev-7-1-–-use-structural-and-semantic-markup-properly-and-validate-code/) and [here](https://stackoverflow.com/questions/7940/how-important-is-w3c-xhtml-css-validation-when-finalizing-work). The site as been generated with [Jekyll](https://jekyllrb.com) and is based on the [John Doe Template](https://github.com/bradleytaunt/john-doe-jekyll). It is inspired by [10kb Club's ideas](https://10kbclub.com/) of a quicker and simpler web.

The site does not track you and runs without any client-side scripts.
