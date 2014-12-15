---
layout: page
title: Люди
comments: true
---

<ul class="author-list">
{% for data in site.data.authors %}
  {% assign author = data[1] %}
  {% assign authorId = data[0] %}
  <li>
    {% if author.avatar contains 'http' %}
    <img src="{{ author.avatar }}" class="bio-photo" alt="{{ author.name }} bio photo"></a>
    {% else %}
    <img src="{{ site.url }}/images/{{ author.avatar }}" class="bio-photo" alt="{{ author.name }} bio photo"></a>
    {% endif %}
    <h2 data-company="{{ author.company }}">{{ author.name }}</h2>
    <p>{{ author.bio }}</p>
    <ul class="post-list">
    {% for post in site.categories.talks %}
      {% if post.author == authorId %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}.</a></li> 
      {% endif %}  
    {% endfor %}
    </ul>
  </li>
{% endfor %}
</ul>