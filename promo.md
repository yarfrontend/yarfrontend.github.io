---
layout: promo
title: 30 сентября 2015
excerpt: 
comments: 
---


<h1>Yaroslavl Frontend Meetup #<span id="num"></span></h1>
<p id="hashtag">#yarfrontend</p>
<p>WiFi SSID: <span id="wifi">Foo</span></p>
<p>WiFi Password: <span id="password">Bar</span></p>

<script>
  var parts = window.location.hash.substr(1).split(',');
  document.getElementById('num').innerHTML = parts[0];
  document.getElementById('wifi').innerHTML = parts[1];
  document.getElementById('password').innerHTML = parts[2];
</script>