<template>
  <div class="font-sans antialiased text-slate-900 dark:text-slate-50 min-h-screen bg-slate-50 dark:bg-dark-900 selection:bg-teal-500/30">
    <Navbar />
    
    <main>
      <Hero />
      <About />
      <Experience />
      <Projects />
      <Services />
      <Testimonials />
      <Contact />
    </main>
    
    <Footer />
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import AOS from 'aos'
import 'aos/dist/aos.css'

import Navbar from './components/Navbar.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Experience from './components/Experience.vue'
import Projects from './components/Projects.vue'
import Services from './components/Services.vue'
import Testimonials from './components/Testimonials.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

onMounted(() => {
  AOS.init({
    duration: 800,
    easing: 'ease-out-cubic',
    once: true,
    offset: 50,
  })
})
</script>
