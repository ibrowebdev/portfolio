<template>
  <section id="contact" class="py-20 bg-slate-50 dark:bg-dark-800 transition-colors">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16" data-aos="fade-up">
        <h2 class="text-3xl md:text-4xl font-bold text-slate-900 dark:text-white mb-4">Get In Touch</h2>
        <div class="w-20 h-1 bg-teal-600 dark:bg-teal-400 mx-auto rounded-full mb-6"></div>
        <p class="text-slate-600 dark:text-slate-400 max-w-2xl mx-auto text-lg">
          Have a project in mind or just want to say hi? Feel free to reach out!
        </p>
      </div>

      <div class="flex flex-col lg:flex-row gap-12 max-w-5xl mx-auto">
        <!-- Contact Info -->
        <div class="lg:w-1/3 space-y-8" data-aos="fade-right">
          <div class="flex items-start gap-4">
            <div class="w-12 h-12 bg-white dark:bg-dark-900 rounded-xl flex items-center justify-center flex-shrink-0 shadow-sm border border-slate-100 dark:border-dark-700">
              <Mail class="w-6 h-6 text-teal-600 dark:text-teal-400" />
            </div>
            <div>
              <h4 class="text-lg font-bold text-slate-800 dark:text-white mb-1">Email</h4>
              <a href="mailto:yusufikeolapo2002@gmail.com" class="text-slate-600 dark:text-slate-400 hover:text-teal-600 dark:hover:text-teal-400 transition-colors">
                yusufikeolapo2002@gmail.com
              </a>
            </div>
          </div>
          
          <div class="flex items-start gap-4">
            <div class="w-12 h-12 bg-white dark:bg-dark-900 rounded-xl flex items-center justify-center flex-shrink-0 shadow-sm border border-slate-100 dark:border-dark-700">
              <MapPin class="w-6 h-6 text-teal-600 dark:text-teal-400" />
            </div>
            <div>
              <h4 class="text-lg font-bold text-slate-800 dark:text-white mb-1">Location</h4>
              <p class="text-slate-600 dark:text-slate-400">
                Remote / Global
              </p>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="lg:w-2/3 bg-white dark:bg-dark-900 p-8 rounded-2xl shadow-sm border border-slate-100 dark:border-dark-700" data-aos="fade-left">
          <form @submit.prevent="submitForm" class="space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium text-slate-700 dark:text-slate-300 mb-2">Name</label>
                <input 
                  type="text" 
                  id="name" 
                  v-model="form.name"
                  required
                  class="w-full px-4 py-3 rounded-lg border border-slate-200 dark:border-dark-700 bg-slate-50 dark:bg-dark-800 text-slate-900 dark:text-white focus:ring-2 focus:ring-teal-500 outline-none transition-shadow"
                  placeholder="John Doe"
                />
              </div>
              <div>
                <label for="email" class="block text-sm font-medium text-slate-700 dark:text-slate-300 mb-2">Email</label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="form.email"
                  required
                  class="w-full px-4 py-3 rounded-lg border border-slate-200 dark:border-dark-700 bg-slate-50 dark:bg-dark-800 text-slate-900 dark:text-white focus:ring-2 focus:ring-teal-500 outline-none transition-shadow"
                  placeholder="john@example.com"
                />
              </div>
            </div>
            <div>
              <label for="subject" class="block text-sm font-medium text-slate-700 dark:text-slate-300 mb-2">Subject</label>
              <select name="subject" v-model="form.subject" id="" class="w-full px-4 py-3 rounded-lg border border-slate-200 dark:border-dark-700 bg-slate-50 dark:bg-dark-800 text-slate-900 dark:text-white focus:ring-2 focus:ring-teal-500 outline-none transition-shadow">
                <option value="">Select subject</option>
                <option value="General Enquiry">General Enquiry</option>
                <option value="Project Request">Project Request</option>
                <option value="Partnership">Partnership</option>
                <option value="Support">Support</option>
              </select>
            </div>
            
            <div>
              <label for="message" class="block text-sm font-medium text-slate-700 dark:text-slate-300 mb-2">Message</label>
              <textarea 
                id="message" 
                rows="5"
                v-model="form.message"
                required
                class="w-full px-4 py-3 rounded-lg border border-slate-200 dark:border-dark-700 bg-slate-50 dark:bg-dark-800 text-slate-900 dark:text-white focus:ring-2 focus:ring-teal-500 outline-none transition-shadow resize-none"
                placeholder="How can I help you?"
              ></textarea>
            </div>
            
            <button 
              type="submit" 
              :disabled="loading"
              class="w-full py-3.5 px-6 rounded-lg bg-teal-600 hover:bg-teal-700 text-white font-medium transition-colors shadow-md shadow-teal-500/20 disabled:opacity-70 disabled:cursor-not-allowed flex items-center justify-center gap-2"
            >
              <span v-if="loading">Sending...</span>
              <template v-else>
                Send Message <Send class="w-4 h-4" />
              </template>
            </button>
            
            <p v-if="successMsg" class="text-green-600 dark:text-green-400 text-sm text-center mt-4">
              {{ successMsg }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import { Mail, MapPin, Send } from 'lucide-vue-next';

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
});

const loading = ref(false);
const successMsg = ref('');

const submitForm = () => {
  loading.value = true;
  successMsg.value = '';
  
  const { name, email, subject, message } = form.value;
  
  // Format the email
  const mailSubject = subject || 'New Contact from Portfolio';
  const mailBody = `Name: ${name}
Email: ${email}

Message:
${message}`;

  // Create mailto link and open it
  const mailtoLink = `mailto:yusufikeolapo2002@gmail.com?subject=${encodeURIComponent(mailSubject)}&body=${encodeURIComponent(mailBody)}`;
  window.location.href = mailtoLink;
  
  successMsg.value = 'Opening your email client...';
  
  setTimeout(() => {
    form.value = { name: '', email: '', subject: '', message: '' };
    loading.value = false;
    successMsg.value = '';
  }, 2000);
};
</script>
