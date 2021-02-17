---
title: James Garner Composer
---

![James Garner's headshot](/assets/images/cover_photo.png)
<div class="image-footnote">© 2018 Gordon Scammell</div>

<div class="carousel carousel-dark carousel-fade col mt-2 slide" data-bs-ride="carousel">
  <div class="carousel-inner">
    {% for quote in site.data.quotes %}
      <div class="{% if forloop.first %}active {% endif %}carousel-item" data-bs-interval="8000">
        <figure class="text-end">
          <blockquote class="blockquote">
            <p class="fs-4">{{ quote.text | markdownify | remove: "<p>" | remove: "</p>" }}</p>
          </blockquote>
          <figcaption class="blockquote-footer fs-6">
            {{ quote.quotee | markdownify | remove: "<p>" | remove: "</p>" }}
          </figcaption>
        </figure>
      </div>
    {% endfor %}
  </div>
</div>

<br>

{% include soundcloud.html track_id="544833195" %}
