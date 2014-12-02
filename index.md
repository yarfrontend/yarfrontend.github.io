---
layout: page
title: 10 Декабря 2014
excerpt: 
comments: true
---

Доклады
-------

<ul class="post-list">
{% for post in site.categories.nearest %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></article></li>
{% endfor %}
</ul>

Когда
-----

Первая встреча пройдет 10 Декабря 2014 в 19:00. Пожалуйста, [зарегистрируйтесь][register], чтобы мы могли оценить
количество участников.

Где
---

Встреча пройдет в новом офисе компании [Тензор][tensor] по адресу: г. Ярославль, ул. Угличская, д. 36.
Центральный вход, угол здания на пересечении улиц Чехова и Угличской.
Маршрут от остановки общественного транспорта указан на карте.

Контактные телефоны: +7 905 136-22-39 Ирина, +7 920 1000-282 Олег

<script type="text/javascript" charset="utf-8" src="//api-maps.yandex.ru/services/constructor/1.0/js/?sid=OaSCkjqQ9MoOIwGeLlFWJiM9GD6Ae8KK&width=600&height=450"></script>

<!--
<ul class="post-list">
{% for post in site.posts limit:10 %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span></a></article></li>
{% endfor %}
</ul>
-->

[register]: /register/
[tensor]: http://tensor.ru/