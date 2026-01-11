---
layout: default
title: Gallery
---

<section class="max-w-5xl mx-auto py-20 px-4">
  <h2 class="text-4xl mb-12 text-center">Our Work</h2>

  <div class="flex justify-center items-center w-full">
    {% for item in site.data.gallery %}
      <div class="relative group w-80 flex-shrink-0">
        <img src="{{ item.image }}"
             alt="{{ item.title }}"
             class="rounded shadow w-full h-64 object-cover">

        <!-- Overlay -->
        <div class="absolute inset-0 bg-black/40 rounded flex items-center justify-center">
          <h3 class="text-xl font-serif text-white text-center px-2">
            {{ item.title }}
          </h3>
        </div>
      </div>
    {% endfor %}
  </div>
</section>

