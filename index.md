---
layout: default
title: Home
---

<section id="home" class="h-[80vh] bg-cover bg-center bg-no-repeat relative flex items-center" style="background-image: url('{{ "/assets/images/hero-bg-1.jpg" | relative_url }}');">
  <!-- Overlay for better text readability -->
  <div class="absolute inset-0 bg-black bg-opacity-25"></div>
  
  <div class="max-w-4xl mx-auto text-center relative z-10">
    <h2 class="text-5xl font-serif mb-6 text-white">
      Handcrafted Wooden Furniture
    </h2>
    <p class="text-lg mb-8 text-white">
      Custom interiors, wardrobes, kitchens & furniture
    </p>
    <a href="#gallery"
       class="px-8 py-3 bg-black text-white hover:bg-gray-800 transition-colors">
      View Our Work
    </a>
  </div>
</section>

<section class="max-w-7xl mx-auto py-20">
  <h3 class="text-3xl mb-10 text-center">Why Choose Us</h3>
  <div class="grid md:grid-cols-3 gap-8">
    <div class="text-center p-6">
      <div class="w-16 h-16 bg-gray-100 rounded-full flex items-center justify-center mx-auto mb-4">
        <i class="fas fa-gem text-2xl text-gray-700"></i>
      </div>
      <h4 class="text-xl font-serif mb-3">Premium Materials</h4>
      <p class="text-gray-600">We source only the finest hardwoods and premium materials, ensuring each piece is built to last generations and maintain its beauty over time.</p>
    </div>
    <div class="text-center p-6">
      <div class="w-16 h-16 bg-gray-100 rounded-full flex items-center justify-center mx-auto mb-4">
        <i class="fas fa-pencil-ruler text-2xl text-gray-700"></i>
      </div>
      <h4 class="text-xl font-serif mb-3">Custom Design</h4>
      <p class="text-gray-600">Every piece is tailored to your unique space and style. We work closely with you to create furniture that perfectly complements your home and lifestyle.</p>
    </div>
    <div class="text-center p-6">
      <div class="w-16 h-16 bg-gray-100 rounded-full flex items-center justify-center mx-auto mb-4">
        <i class="fas fa-hammer text-2xl text-gray-700"></i>
      </div>
      <h4 class="text-xl font-serif mb-3">Trusted Craftsmanship</h4>
      <p class="text-gray-600">With decades of experience, our skilled artisans combine traditional techniques with modern precision to deliver exceptional quality in every detail.</p>
    </div>
  </div>
</section>

<section id="gallery" class="max-w-7xl mx-auto py-20">
  <h2 class="text-4xl mb-12 text-center">Gallery</h2>

  <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
    {% for item in site.data.gallery %}
      <div class="relative group">
        <img src="{{ item.image }}"
             alt="{{ item.title }}"
             class="rounded shadow w-full object-cover">
        <!-- Overlay for text -->
        <div class="absolute inset-0 bg-black bg-opacity-20 rounded flex items-center justify-center">
          <h3 class="text-xl font-serif text-white text-center px-2">{{ item.title }}</h3>
        </div>
      </div>
    {% endfor %}
  </div>
</section>

<section id="testimonials" class="max-w-5xl mx-auto py-20 relative">
  <h2 class="text-4xl mb-12 text-center">Testimonials</h2>

  <div class="relative overflow-hidden">
    <div id="testimonials-carousel" class="flex transition-transform duration-500 ease-in-out">
      {% for t in site.data.testimonials %}
        <div class="min-w-full px-4">
          <div class="border p-8 text-center max-w-2xl mx-auto">
            <p class="text-lg mb-4">"{{ t.text }}"</p>
            <p class="text-sm text-gray-600">— {{ t.name }}</p>
          </div>
        </div>
      {% endfor %}
    </div>
  </div>

  <!-- Navigation Arrows -->
  <button id="prev-testimonial" class="absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 bg-white border border-gray-300 rounded-full p-2 shadow-lg hover:bg-gray-100 transition-colors">
    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
    </svg>
  </button>
  <button id="next-testimonial" class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 bg-white border border-gray-300 rounded-full p-2 shadow-lg hover:bg-gray-100 transition-colors">
    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
    </svg>
  </button>
</section>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const carousel = document.getElementById('testimonials-carousel');
  const prevBtn = document.getElementById('prev-testimonial');
  const nextBtn = document.getElementById('next-testimonial');
  const testimonials = carousel.children;
  let currentIndex = 0;
  let autoAdvanceInterval;

  function showTestimonial(index) {
    if (index < 0) index = testimonials.length - 1;
    if (index >= testimonials.length) index = 0;
    
    currentIndex = index;
    carousel.style.transform = `translateX(-${index * 100}%)`;
  }

  function nextTestimonial() {
    showTestimonial(currentIndex + 1);
  }

  function prevTestimonial() {
    showTestimonial(currentIndex - 1);
  }

  function startAutoAdvance() {
    autoAdvanceInterval = setInterval(nextTestimonial, 7500);
  }

  function stopAutoAdvance() {
    clearInterval(autoAdvanceInterval);
  }

  // Event listeners
  nextBtn.addEventListener('click', () => {
    nextTestimonial();
    stopAutoAdvance();
    startAutoAdvance();
  });

  prevBtn.addEventListener('click', () => {
    prevTestimonial();
    stopAutoAdvance();
    startAutoAdvance();
  });

  // Start auto-advance
  startAutoAdvance();

  // Pause on hover
  carousel.addEventListener('mouseenter', stopAutoAdvance);
  carousel.addEventListener('mouseleave', startAutoAdvance);
});
</script>

<section id="contact" class="max-w-xl mx-auto py-20">
  <h2 class="text-4xl mb-8 text-center">Contact Us</h2>

  <div class="text-center space-y-6">
    <div class="space-y-4">
      <div class="flex items-center justify-center space-x-3">
        <i class="fas fa-phone text-gray-600"></i>
        <a href="tel:+1234567890" class="text-lg hover:text-gray-600 transition-colors">+1 (234) 567-890</a>
      </div>
      <div class="flex items-center justify-center space-x-3">
        <i class="fas fa-envelope text-gray-600"></i>
        <a href="mailto:info@furniturecompany.com" class="text-lg hover:text-gray-600 transition-colors">info@furniturecompany.com</a>
      </div>
    </div>

    <div class="pt-4 border-t border-gray-200">
      <!-- <p class="text-sm text-gray-600 mb-4">Follow Us</p> -->
      <div class="flex justify-center space-x-6">
        <a href="https://www.facebook.com/woodenworks.online" class="text-gray-500 hover:text-blue-600 transition-colors" aria-label="Facebook">
          <i class="fab fa-facebook-f text-xl"></i>
        </a>
        <a href="https://www.instagram.com/woodenworks.online" class="text-gray-500 hover:text-pink-600 transition-colors" aria-label="Instagram">
          <i class="fab fa-instagram text-xl"></i>
        </a>
        <a href="https://www.twitter.com/woodenworks.online" class="text-gray-500 hover:text-blue-400 transition-colors" aria-label="Twitter">
          <i class="fab fa-twitter text-xl"></i>
        </a>
        <a href="https://www.linkedin.com/company/woodenworks" class="text-gray-500 hover:text-blue-700 transition-colors" aria-label="LinkedIn">
          <i class="fab fa-linkedin-in text-xl"></i>
        </a>
        <a href="https://www.pinterest.com/woodenworks" class="text-gray-500 hover:text-red-600 transition-colors" aria-label="Pinterest">
          <i class="fab fa-pinterest text-xl"></i>
        </a>
      </div>
    </div>
  </div>
</section>
