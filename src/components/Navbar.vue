<template>
  <nav 
    class="fixed w-full top-0 z-50 transition-all duration-300 backdrop-blur-md"
    :class="{ 'bg-white/80 dark:bg-dark-900/80 shadow-md py-4': scrolled, 'bg-transparent py-6': !scrolled }"
  >
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center">
        <!-- Logo -->
        <a href="#home" class="text-2xl font-bold tracking-tighter text-teal-600 dark:text-teal-400">
          Ibrohim<span class="text-slate-800 dark:text-white">.dev</span>
        </a>

        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center space-x-8">
          <a v-for="link in links" :key="link.name" :href="link.href" class="text-sm font-medium text-slate-600 hover:text-teal-600 dark:text-slate-300 dark:hover:text-teal-400 transition-colors">
            {{ link.name }}
          </a>
          
          <!-- Dark Mode Toggle -->
          <button @click="toggleDarkMode" class="p-2 rounded-full hover:bg-slate-100 dark:hover:bg-dark-800 transition-colors">
            <Moon v-if="!isDark" class="w-5 h-5 text-slate-600" />
            <Sun v-else class="w-5 h-5 text-amber-400" />
          </button>

          <a href="/public/Ibrohim-Yusuf Resume.pdf" download class="px-5 py-2.5 rounded-lg bg-teal-600 hover:bg-teal-700 text-white text-sm font-medium transition-colors shadow-lg shadow-teal-500/30">
            Download CV
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <div class="md:hidden flex items-center gap-4">
          <button @click="toggleDarkMode" class="p-2 rounded-full hover:bg-slate-100 dark:hover:bg-dark-800 transition-colors">
            <Moon v-if="!isDark" class="w-5 h-5 text-slate-600" />
            <Sun v-else class="w-5 h-5 text-amber-400" />
          </button>
          <button @click="mobileMenuOpen = !mobileMenuOpen" class="text-slate-600 dark:text-slate-300">
            <Menu v-if="!mobileMenuOpen" class="w-6 h-6" />
            <X v-else class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu -->
    <div v-show="mobileMenuOpen" class="md:hidden absolute top-full left-0 w-full bg-white dark:bg-dark-900 border-b border-slate-200 dark:border-dark-800 shadow-xl">
      <div class="px-4 py-4 flex flex-col space-y-4">
        <a 
          v-for="link in links" 
          :key="link.name" 
          :href="link.href" 
          @click="mobileMenuOpen = false"
          class="text-base font-medium text-slate-600 hover:text-teal-600 dark:text-slate-300 dark:hover:text-teal-400"
        >
          {{ link.name }}
        </a>
        <a href="/public/Ibrohim-Yusuf Resume.pdf" download class="inline-block text-center w-full px-5 py-3 rounded-lg bg-teal-600 hover:bg-teal-700 text-white font-medium transition-colors">
          Download CV
        </a>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { Menu, X, Moon, Sun } from 'lucide-vue-next';

const scrolled = ref(false);
const mobileMenuOpen = ref(false);
const isDark = ref(true); // Default dark

const links = [
  { name: 'Home', href: '#home' },
  { name: 'About', href: '#about' },
  { name: 'Experience', href: '#experience' },
  { name: 'Projects', href: '#projects' },
  { name: 'Contact', href: '#contact' },
];

const toggleDarkMode = () => {
  isDark.value = !isDark.value;
  if (isDark.value) {
    document.documentElement.classList.add('dark');
    localStorage.setItem('theme', 'dark');
  } else {
    document.documentElement.classList.remove('dark');
    localStorage.setItem('theme', 'light');
  }
};

const handleScroll = () => {
  scrolled.value = window.scrollY > 20;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  // Check local storage for theme
  if (localStorage.getItem('theme') === 'light' || (!localStorage.getItem('theme') && window.matchMedia('(prefers-color-scheme: light)').matches)) {
    isDark.value = false;
    document.documentElement.classList.remove('dark');
  } else {
    document.documentElement.classList.add('dark');
  }
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>
