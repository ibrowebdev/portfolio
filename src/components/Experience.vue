<template>
  <section id="experience" class="py-20 bg-slate-50 dark:bg-dark-800 transition-colors">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">Experience</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full"></div>
      </div>

      <div class="relative border-l-2 border-teal-200 dark:border-teal-900/50 ml-3 md:ml-6">
        <div 
          v-for="(item, index) in experience" 
          :key="item.id"
          class="mb-12 ml-8 md:ml-12 relative"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <!-- Timeline Dot -->
          <span class="absolute -left-[41px] md:-left-[57px] top-1 w-5 h-5 rounded-full bg-teal-500 border-4 border-slate-50 dark:border-dark-800 shadow-sm"></span>
          
          <div class="bg-white dark:bg-dark-900 p-6 rounded-2xl shadow-sm border border-slate-100 dark:border-dark-700 hover:shadow-md transition-shadow">
            <div class="flex flex-col md:flex-row md:items-center justify-between mb-2 gap-2">
              <h3 class="text-xl font-bold text-slate-800 dark:text-slate-100">{{ item.role }}</h3>
              <span class="inline-block px-3 py-1 rounded-full text-xs font-medium bg-teal-100 text-teal-800 dark:bg-teal-900/30 dark:text-teal-300 w-fit">
                {{ item.date }}
              </span>
            </div>
            <h4 class="text-lg text-teal-600 dark:text-teal-400 font-medium mb-4">{{ item.company }}</h4>
            <p class="text-slate-600 dark:text-slate-400 leading-relaxed" v-html="item.description"></p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { experience } from '../data/experience';
</script>
