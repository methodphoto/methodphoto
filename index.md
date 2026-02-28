---
layout: default
title: Galleries
---
{% assign carousel_images = site.static_files
  | where_exp: "file", "file.path contains '/assets/carousel/'"
  | where_exp: "file", "'.jpg|.jpeg|.png|.webp|.avif' contains file.extname"
  | sort: "path" %}

# News

## Featured Gallery

### I Am the Sea Alone, 2026

<div style="padding:56.25% 0 0 0;position:relative;">
	<iframe src="https://player.vimeo.com/video/1165109561?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479&amp;autoplay=1" frameborder="0" allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share" referrerpolicy="strict-origin-when-cross-origin" style="position:absolute;top:0;left:0;width:100%;height:100%;" title="I Am the Sea Alone"></iframe>
</div>
<script src="https://player.vimeo.com/api/player.js"></script>

{% include gallery %}
