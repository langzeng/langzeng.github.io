---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<div class="posts">
  {% for post in site.posts %}
  {% if post.sticky %}
  <div class="post">
    <h1 class="post-title">
      <a href="{{ post.url | absolute_url }}">
        <p style="font-size:20px">{{ post.title }}</p>
      </a>
    </h1>
  </div>
  {% endif %}
  {% endfor %}
</div>
