<template>
  <section id="testimonials" class="py-20 bg-white dark:bg-dark-900 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">Testimonials</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full mb-6"></div>
        <p class="text-slate-600 dark:text-slate-400 max-w-2xl mx-auto text-lg">
          What people are saying about my work.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div 
          v-for="(testimonial, index) in testimonials" 
          :key="testimonial.id"
          class="bg-slate-50 dark:bg-dark-800 rounded-2xl p-8 border border-slate-100 dark:border-dark-700 relative"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <Quote class="absolute top-6 right-6 w-8 h-8 text-teal-500/20 dark:text-teal-400/10" />
          
          <div class="flex items-center gap-4 mb-6">
            <img :src="testimonial.image" :alt="testimonial.name" class="w-14 h-14 rounded-full object-cover border-2 border-white dark:border-dark-700 shadow-sm" />
            <div>
              <h4 class="text-lg font-bold text-slate-800 dark:text-white">{{ testimonial.name }}</h4>
              <p class="text-sm text-teal-600 dark:text-teal-400 font-medium">{{ testimonial.company }}</p>
            </div>
          </div>
          
          <p class="text-slate-600 dark:text-slate-400 italic leading-relaxed text-sm">
            "{{ testimonial.text }}"
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { testimonials } from '../data/testimonials';
import { Quote } from 'lucide-vue-next';
</script>
