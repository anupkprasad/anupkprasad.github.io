---
permalink: /gallery/
title: "Gallery"
author_profile: true
layout: single
redirect_from:
  - /gallery.html
---

<style>
/* Simple responsive gallery */
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 12px;
}
.gallery-item {
  overflow: hidden;
  background: #f7f7f7;
  border-radius: 6px;
}
.gallery-item img {
  display: block;
  width: 100%;
  height: auto;
  object-fit: cover;
}
.gallery-intro { margin-bottom: 1rem; }
</style>

## Gallery

<p class="gallery-intro">A scrollable gallery of academic images. Add image files to <code>images/gallery/</code> and they will appear below. Supported image types: jpg, jpeg, png, gif, webp.</p>

{% assign gallery_files = site.static_files | where_exp: "file", "file.path contains '/images/gallery/'" %}

{% if gallery_files.size > 0 %}
<div class="gallery-grid">
  {% for file in gallery_files %}
    {% assign ext = file.extname | downcase %}
    {% if ext == '.png' or ext == '.jpg' or ext == '.jpeg' or ext == '.gif' or ext == '.webp' %}
      <figure class="gallery-item">
        <img src="{{ file.path | relative_url }}" alt="{{ file.name }}">
      </figure>
    {% endif %}
  {% endfor %}
</div>
{% else %}
<p>No images found in <code>images/gallery/</code>. Create that directory and add images (e.g., <code>images/gallery/your_image.png</code>) to populate the gallery.</p>
{% endif %}

<!-- EOF -->
