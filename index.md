---
title: Home
layout: default
---

hello
v3'


<div id='dogs'>
  {% for a in site.test %}
    
      <a href='{{ a.url }}'>{{ a.title }}</a>
      <br/>
  {% endfor %}
</div>


<hr/>


[test/index.html](_test/index.html)
<br/>

[test/index.md](_test/index.md)
