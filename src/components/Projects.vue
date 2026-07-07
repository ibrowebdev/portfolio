<template>
  <section id="projects" class="py-20 bg-white dark:bg-dark-900 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-12" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">Featured Projects</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full mb-8"></div>
        
        <!-- Filters -->
        <div class="flex flex-wrap justify-center gap-3">
          <button 
            v-for="filter in filters" 
            :key="filter"
            @click="activeFilter = filter"
            class="px-4 py-2 rounded-full text-sm font-medium transition-colors"
            :class="activeFilter === filter ? 'bg-teal-600 text-white shadow-md' : 'bg-slate-100 text-slate-600 hover:bg-slate-200 dark:bg-dark-800 dark:text-slate-300 dark:hover:bg-dark-700'"
          >
            {{ filter }}
          </button>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in filteredProjects" 
          :key="project.id"
          class="bg-white dark:bg-dark-900 rounded-2xl overflow-hidden border border-slate-200 dark:border-dark-700 hover:shadow-xl hover:-translate-y-1 transition-all duration-300 group flex flex-col"
          data-aos="fade-up"
          :data-aos-delay="index * 100"
        >
          <!-- Image Container -->
          <div class="relative overflow-hidden aspect-video">
            <div class="absolute inset-0 bg-slate-900/20 group-hover:bg-transparent transition-colors z-10"></div>
            <img 
              :src="project.image" 
              :alt="project.title" 
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
            />
          </div>
          
          <!-- Content -->
          <div class="p-6 flex flex-col flex-grow">
            <h3 class="text-xl font-bold text-slate-800 dark:text-white mb-2 group-hover:text-teal-600 dark:group-hover:text-teal-400 transition-colors">
              {{ project.title }}
            </h3>
            <p class="text-slate-600 dark:text-slate-400 mb-6 text-sm flex-grow">
              {{ project.description }}
            </p>
            
            <!-- Tech Stack -->
            <div class="flex flex-wrap gap-2 mb-6 mt-auto">
              <span 
                v-for="tech in project.tech" 
                :key="tech"
                class="px-2.5 py-1 text-xs font-medium bg-slate-100 text-slate-600 dark:bg-dark-800 dark:text-slate-300 rounded-md"
              >
                {{ tech }}
              </span>
            </div>
            
            <!-- Links -->
            <div class="flex items-center gap-4 pt-4 border-t border-slate-100 dark:border-dark-800">
              <a 
                :href="project.liveUrl" 
                target="_blank" 
                class="flex items-center gap-2 text-sm font-medium text-slate-700 hover:text-teal-600 dark:text-slate-300 dark:hover:text-teal-400 transition-colors"
              >
                <ExternalLink class="w-4 h-4" /> Live Demo
              </a>
              <a 
                :href="project.githubUrl" 
                target="_blank" 
                class="flex items-center gap-2 text-sm font-medium text-slate-700 hover:text-teal-600 dark:text-slate-300 dark:hover:text-teal-400 transition-colors"
              >
                <Github class="w-4 h-4" /> Source
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';
import { ExternalLink, Github } from 'lucide-vue-next';
import { projects } from '../data/projects';

const activeFilter = ref('All');

// Extract unique technologies for filters
const filters = computed(() => {
  const allTechs = projects.flatMap(p => p.tech);
  const uniqueTechs = [...new Set(allTechs)].sort();
  return ['All', ...uniqueTechs];
});

const filteredProjects = computed(() => {
  if (activeFilter.value === 'All') {
    return projects;
  }
  return projects.filter(project => project.tech.includes(activeFilter.value));
});
</script>
