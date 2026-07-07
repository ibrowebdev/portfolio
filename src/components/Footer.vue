<template>
  <footer class="bg-white dark:bg-dark-900 border-t border-slate-100 dark:border-dark-800 py-12 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row justify-between items-center gap-6">
      
      <div class="text-center md:text-left">
        <a href="#home" class="text-xl font-bold tracking-tighter text-teal-600 dark:text-teal-400 mb-2 block">
          Yusuf<span class="text-slate-800 dark:text-white">.dev</span>
        </a>
        <p class="text-slate-500 dark:text-slate-400 text-sm">
          &copy; {{ currentYear }} Yusuf Ibrohim. All rights reserved.
        </p>
      </div>

      <div class="flex items-center gap-6">
        <a href="https://github.com/ibrowebdev" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-slate-900 dark:hover:text-white transition-colors">
          <span class="sr-only">GitHub</span>
          <Github class="w-5 h-5" />
        </a>
        <a href="https://www.linkedin.com/in/yusuf-ibrohim-aa291a351/" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-[#0a66c2] transition-colors">
          <span class="sr-only">LinkedIn</span>
          <Linkedin class="w-5 h-5" />
        </a>
        <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-blue-400 transition-colors">
          <span class="sr-only">Twitter</span>
          <Twitter class="w-5 h-5" />
        </a>
      </div>
      
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue';
import { Github, Linkedin, Twitter } from 'lucide-vue-next';

const currentYear = computed(() => new Date().getFullYear());
</script>
