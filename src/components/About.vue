<template>
  <section id="about" class="py-20 bg-white dark:bg-dark-900 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">About Me</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full"></div>
      </div>

      <div class="flex flex-col lg:flex-row gap-12 items-center">
        <!-- Bio -->
        <div class="lg:w-1/2" data-aos="fade-right">
          <h3 class="text-2xl font-bold text-slate-800 dark:text-slate-100 mb-4">
            A passionate developer bridging the gap between design and robust backend systems.
          </h3>
          <p class="text-slate-600 dark:text-slate-400 mb-6 leading-relaxed text-lg">
            With several years of experience in the tech industry, I specialize in building end-to-end web applications. 
            My journey started with raw PHP and jQuery, evolving into modern stacks using Laravel, Livewire, Alpine.js, Vue.js. 
            I love architecting databases, creating seamless APIs, and bringing pixel-perfect designs to life.
          </p>
          <div class="grid grid-cols-2 gap-6 mt-8">
            <div class="border border-slate-200 dark:border-dark-700 rounded-xl p-6 text-center">
              <h4 class="text-4xl font-bold text-teal-600 dark:text-teal-400 mb-2">3+</h4>
              <p class="text-slate-500 dark:text-slate-400 font-medium">Years Experience</p>
            </div>
            <div class="border border-slate-200 dark:border-dark-700 rounded-xl p-6 text-center">
              <h4 class="text-4xl font-bold text-teal-600 dark:text-teal-400 mb-2">10</h4>
              <p class="text-slate-500 dark:text-slate-400 font-medium">Projects</p>
            </div>
          </div>
        </div>

        <!-- Skills -->
        <div class="lg:w-1/2 w-full" data-aos="fade-left">
          <h3 class="text-xl font-bold text-slate-800 dark:text-slate-100 mb-6 text-center lg:text-left">Tech Stack & Tools</h3>
          <div class="grid grid-cols-2 sm:grid-cols-3 gap-4">
            <div 
              v-for="skill in skills" 
              :key="skill.name"
              class="flex flex-col items-center justify-center p-4 rounded-xl bg-slate-50 dark:bg-dark-800 border border-slate-100 dark:border-dark-700 hover:border-teal-500 dark:hover:border-teal-500 transition-colors group cursor-default"
            >
              <component :is="getIcon(skill.icon)" class="w-8 h-8 mb-3 text-slate-400 group-hover:text-teal-500 transition-colors" />
              <span class="text-sm font-medium text-slate-700 dark:text-slate-300">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { skills } from '../data/skills';
import { Server, FileCode, LayoutTemplate, Code, Database, Palette, Network, GitBranch, Box } from 'lucide-vue-next';

const icons = {
  'server': Server,
  'file-code': FileCode,
  'layout-template': LayoutTemplate,
  'code': Code,
  'database': Database,
  'palette': Palette,
  'network': Network,
  'git-branch': GitBranch,
  'box': Box,
};

const getIcon = (name) => {
  return icons[name] || Code;
};
</script>
