---
layout: default
title: Testimonials
---

<section class="max-w-5xl mx-auto py-20">
  <h2 class="text-4xl mb-12 text-center">Testimonials</h2>

  {% for t in site.data.testimonials %}
    <div class="border p-6 mb-6">
      <p>"{{ t.text }}"</p>
      <p class="mt-2 text-sm text-gray-600">— {{ t.name }}</p>
    </div>
  {% endfor %}
</section>
