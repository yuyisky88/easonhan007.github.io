---
layout: default
title: 乙醇的blog
tagline: 
section: index
---
{% include JB/setup %}

<ul class="post-list">
  {% if site.posts.size == 0 %}
    <h2>No post found</h2>
  {% else %}
    {% for post in site.posts %}
      <li>
        <h3>
          <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
        </h3>
        <span class="visible-md-inline visible-lg-inline">
          {{ post.date | date_to_string }}
        </span>
      </li>
    {% endfor %}
  {% endif %}
</ul>


