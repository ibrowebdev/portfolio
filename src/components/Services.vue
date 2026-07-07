<template>
  <section id="services" class="py-20 bg-slate-50 dark:bg-dark-800 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">My Services</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full mb-6"></div>
        <p class="text-slate-600 dark:text-slate-400 max-w-2xl mx-auto text-lg">
          What I can do for you and your business.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="service.id"
          class="bg-white dark:bg-dark-900 rounded-2xl p-8 border border-slate-100 dark:border-dark-700 hover:border-teal-500 dark:hover:border-teal-500 hover:shadow-xl transition-all duration-300 group"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <div class="w-14 h-14 bg-teal-50 dark:bg-teal-900/20 rounded-xl flex items-center justify-center mb-6 group-hover:scale-110 group-hover:bg-teal-600 transition-all duration-300">
            <component :is="getIcon(service.icon)" class="w-7 h-7 text-teal-600 dark:text-teal-400 group-hover:text-white transition-colors" />
          </div>
          <h3 class="text-xl font-bold text-slate-800 dark:text-white mb-3">{{ service.title }}</h3>
          <p class="text-slate-600 dark:text-slate-400 leading-relaxed text-sm">
            {{ service.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { services } from '../data/services';
import { Layout, Server, CodeSquare } from 'lucide-vue-next';

const icons = {
  'layout': Layout,
  'server': Server,
  'code-square': CodeSquare,
};

const getIcon = (name) => {
  return icons[name] || Layout;
};
</script>
