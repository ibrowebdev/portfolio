<template>
  <section id="home" class="min-h-screen flex items-center pt-20 overflow-hidden relative">
    <!-- Background Decor -->
    <div class="absolute top-1/4 left-10 w-72 h-72 bg-teal-500/10 dark:bg-teal-500/20 rounded-full blur-3xl -z-10 animate-pulse"></div>
    <div class="absolute bottom-1/4 right-10 w-96 h-96 bg-blue-500/10 dark:bg-blue-500/10 rounded-full blur-3xl -z-10"></div>
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
      <div class="flex flex-col-reverse lg:flex-row items-center justify-between gap-12">
        
        <!-- Text Content -->
        <div class="lg:w-1/2 flex flex-col items-center lg:items-start text-center lg:text-left" data-aos="fade-up">
          <p class="text-teal-600 dark:text-teal-400 font-medium tracking-wide mb-3 flex items-center gap-2">
            <span class="w-8 h-[2px] bg-teal-600 dark:bg-teal-400"></span>
            Hello, World! I am
          </p>
          <h1 class="text-5xl lg:text-7xl font-bold text-slate-900 dark:text-white leading-tight mb-4">
            Yusuf Ibrohim
          </h1>
          <h2 class="text-2xl lg:text-3xl text-slate-600 dark:text-slate-300 font-medium mb-6">
            Fullstack <span class="text-teal-600 dark:text-teal-400">Laravel</span> Developer
          </h2>
          <p class="text-slate-500 dark:text-slate-400 mb-8 max-w-lg text-lg">
            I craft scalable web applications and seamless user experiences. Passionate about writing clean code and building products that make a difference.
          </p>
          
          <div class="flex flex-wrap items-center gap-4">
            <a href="#projects" class="px-8 py-3.5 rounded-lg bg-teal-600 hover:bg-teal-700 text-white font-medium transition-colors shadow-lg shadow-teal-500/30">
              View Projects
            </a>
            <a href="#contact" class="px-8 py-3.5 rounded-lg border border-slate-300 dark:border-dark-700 hover:border-teal-600 dark:hover:border-teal-400 text-slate-700 dark:text-slate-300 hover:text-teal-600 dark:hover:text-teal-400 font-medium transition-colors">
              Contact Me
            </a>
          </div>

          <div class="flex items-center gap-6 mt-10">
            <a href="https://github.com/ibrowebdev" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-slate-900 dark:hover:text-white transition-colors">
              <Github class="w-6 h-6" />
            </a>
            <a href="https://www.linkedin.com/in/yusuf-ibrohim-aa291a351/" target="_blank" rel="noopener noreferrer" class="text-slate-400 hover:text-[#0a66c2] transition-colors">
              <Linkedin class="w-6 h-6" />
            </a>
            <a href="mailto:yusufikeolapo2002@gmail.com" class="text-slate-400 hover:text-red-500 transition-colors">
              <Mail class="w-6 h-6" />
            </a>
          </div>
        </div>

        <!-- Avatar -->
        <div class="lg:w-1/2 flex justify-center lg:justify-end relative" data-aos="fade-left" data-aos-delay="200">
          <div class="relative w-72 h-72 lg:w-96 lg:h-96">
            <div class="absolute inset-0 rounded-full border-2 border-teal-600/30 border-dashed animate-[spin_10s_linear_infinite]"></div>
            <div class="rounded-full w-full h-full flex items-center justify-center bg-gradient-to-br from-slate-50 to-slate-100 dark:from-dark-800 dark:to-dark-900 p-12 shadow-2xl dark:shadow-teal-900/20 border-4 border-white dark:border-dark-700 relative overflow-hidden group">
              <div class="absolute inset-0 bg-teal-500/5 group-hover:bg-teal-500/10 transition-colors duration-500"></div>
              <div class="absolute -top-10 -right-10 w-40 h-40 bg-teal-500/10 blur-2xl rounded-full"></div>
              <div class="absolute -bottom-10 -left-10 w-40 h-40 bg-blue-500/10 blur-2xl rounded-full"></div>
              <Code2 class="w-full h-full text-teal-600 dark:text-teal-400 opacity-80 drop-shadow-sm group-hover:scale-105 transition-transform duration-500" />
            </div>
            <!-- Decorative badge -->
            <div class="absolute bottom-6 right-6 bg-white dark:bg-dark-800 p-3 rounded-xl shadow-lg border border-slate-100 dark:border-dark-700 animate-bounce">
              <span class="text-2xl">👨‍💻</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Github, Linkedin, Mail, Code2 } from 'lucide-vue-next';
</script>
