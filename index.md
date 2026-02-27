---
layout: default
title: Galleries
---
{% assign carousel_images = site.static_files
  | where_exp: "file", "file.path contains '/assets/carousel/'"
  | where_exp: "file", "file.extname == '.jpg' or file.extname == '.jpeg' or file.extname == '.png' or file.extname == '.webp' or file.extname == '.avif'"
  | sort: "path" %}

# News

## Featured Gallery

### I'm Lost at Sea, Don't Bother Me, 2024

{% if carousel_images.size > 0 %}
<div class="home-carousel" data-carousel>
  <button class="home-carousel__arrow home-carousel__arrow--prev" type="button" aria-label="Previous image" data-carousel-prev>&#8592;</button>
  <button class="home-carousel__arrow home-carousel__arrow--next" type="button" aria-label="Next image" data-carousel-next>&#8594;</button>
  {% for image in carousel_images %}
    <img
      src="{{ image.path | relative_url }}"
      alt=""
      class="home-carousel__slide{% if forloop.first %} is-active{% endif %}"
      data-carousel-slide
      {% unless forloop.first %}loading="lazy"{% endunless %}>
  {% endfor %}
</div>
<script>
  (function () {
    var carousel = document.querySelector("[data-carousel]");
    if (!carousel) return;
    var slides = Array.prototype.slice.call(carousel.querySelectorAll("[data-carousel-slide]"));
    var prev = carousel.querySelector("[data-carousel-prev]");
    var next = carousel.querySelector("[data-carousel-next]");
    if (slides.length < 2) {
      prev.hidden = true;
      next.hidden = true;
      return;
    }
    var current = 0;
    var show = function (index) {
      slides[current].classList.remove("is-active");
      current = (index + slides.length) % slides.length;
      slides[current].classList.add("is-active");
    };
    prev.addEventListener("click", function () { show(current - 1); });
    next.addEventListener("click", function () { show(current + 1); });
  })();
</script>
{% else %}
[![I'm Lost at Sea, Don't Bother Me](im-lost-at-sea-dont-bother-me/im-lost-at-sea-dont-bother-me-12.webp)](im-lost-at-sea-dont-bother-me/)
{% endif %}

Three images from this series showed at [The Original Gallery](https://www.londonphotography.org.uk/upcoming/2025/02/19/lip-crouch-end-annual-exhibition/) in Crouch End and [Framed prints](im-lost-at-sea-dont-bother-me/) are available.


{% include gallery %}
