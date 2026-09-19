<script setup lang="ts">
import { ref, reactive, onMounted } from 'vue'

const isDark = ref<boolean>(true)
const mobileMenuOpen = ref<boolean>(false)
const submitted = ref<boolean>(false)

const profile = reactive({
  name: 'Jericho',
  title: 'A boy who loves to play games',
  bio: 'A 4th year Computer Engineering student passionate about building scalable web applications with clean, typed code and modern interfaces.'
})

const navLinks = [
  { label: 'About', href: '#about' },
  { label: 'Skills', href: '#skills' },
  { label: 'Projects', href: '#projects' },
  { label: 'Contact', href: '#contact' }
]

const aboutCards = [
  { title: 'Game Lover', description: 'A passionate gamer who enjoys exploring new worlds and challenging games.' },
  { title: 'Love Drawing', description: 'A creative individual who enjoys expressing ideas through visual art.' },
  { title: 'Love Cooking', description: 'A culinary enthusiast who enjoys creating delicious meals from scratch.' }
]

const skills = [
  { name: 'Cooking', level: 'newbie', icon: '🟢' },
  { name: 'TypeScript', level: 'newbie', icon: '📘' },
  { name: 'Tailwind CSS', level: 'newbie', icon: '🎨' },
  { name: 'JavaScript (ES6+)', level: 'newbie', icon: '⚡' },
  { name: 'Vite', level: 'newbie', icon: '⚡' },
  { name: 'Git & GitHub', level: 'newbie', icon: '🐙' },
  { name: 'REST APIs', level: 'newbie', icon: '🔌' },
  { name: 'HTML5 / CSS3', level: 'newbie', icon: '🌐' }
]

const projects = [
  {
    id: 1,
    title: 'Portfolio-Jericho',
    category: 'Web Portfolio',
    description: 'A modern, responsive portfolio web app built specifically with Vue 3, TypeScript, and Tailwind CSS.',
    techStack: ['Vue 3', 'TypeScript', 'Tailwind CSS', 'Vite'],
    image: 'https://placehold.co/600x400/0f172a/34d399?text=Portfolio+App',
    github: 'https://github.com/nikkoo11/Portfolio-Jericho',
    liveDemo: '#hero'
  },
  {
    id: 2,
    title: 'Line Follower Robot',
    category: 'Robotics Project',
    description: 'A simple line follower robot built with Arduino and sensors.',
    techStack: ['Arduino', 'C++', 'Sensors', 'Robotics'],
    image: 'https://placehold.co/600x400/0f172a/facc15?text=Line+Follower+Robot',
    github: 'https://github.com/nikkoo11',
    liveDemo: '#'
  },
  {
    id: 3,
    title: 'Microcontroller Projects',
    category: 'Arduino & Embedded Systems',
    description: 'A collection of microcontroller-based projects demonstrating various applications and functionalities.',
    techStack: ['Arduino', 'C++', 'Embedded Systems', 'IoT'],
    image: 'https://placehold.co/600x400/0f172a/38bdf8?text=Microcontroller+Projects',
    github: 'https://github.com/nikkoo11',
    liveDemo: '#'
  }
]

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const toggleDarkMode = () => {
  isDark.value = !isDark.value
  if (isDark.value) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}

onMounted(() => {
  document.documentElement.classList.add('dark')
})

const handleSubmit = () => {
  submitted.value = true
  form.name = ''
  form.email = ''
  form.subject = ''
  form.message = ''
  setTimeout(() => {
    submitted.value = false
  }, 5000)
}
</script>

<template>
  <div class="bg-slate-50 text-slate-800 dark:bg-slate-950 dark:text-slate-100 transition-colors duration-300 min-h-screen scroll-smooth">
    <!-- Navigation Bar -->
    <header class="fixed top-0 left-0 right-0 z-50 bg-white/80 dark:bg-slate-900/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-800 transition-colors">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
        <a href="#hero" class="text-xl font-bold bg-gradient-to-r from-emerald-500 to-cyan-500 bg-clip-text text-transparent flex items-center gap-2">
          <span class="p-1.5 bg-emerald-500/10 rounded-lg text-emerald-500 font-mono text-sm">&lt;/&gt;</span>
          {{ profile.name }}
        </a>

        <!-- Desktop Navigation Links -->
        <nav class="hidden md:flex items-center space-x-8 text-sm font-medium">
          <a v-for="link in navLinks" :key="link.href" :href="link.href" class="hover:text-emerald-500 transition-colors">
            {{ link.label }}
          </a>
        </nav>

        <!-- Actions: Theme Switcher & Mobile Menu Toggle -->
        <div class="flex items-center space-x-4">
          <button @click="toggleDarkMode" class="p-2 rounded-xl bg-slate-100 dark:bg-slate-800 hover:scale-105 transition-transform" aria-label="Toggle Theme">
            <svg v-if="isDark" class="w-5 h-5 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path></svg>
            <svg v-else class="w-5 h-5 text-slate-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path></svg>
          </button>

          <!-- Mobile Menu Button -->
          <button @click="mobileMenuOpen = !mobileMenuOpen" class="md:hidden p-2 rounded-xl bg-slate-100 dark:bg-slate-800">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path v-if="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Navigation Drawer -->
      <div v-if="mobileMenuOpen" class="md:hidden bg-white dark:bg-slate-900 border-b border-slate-200 dark:border-slate-800 px-4 pt-2 pb-6 space-y-2">
        <a v-for="link in navLinks" :key="link.href" :href="link.href" @click="mobileMenuOpen = false" class="block px-3 py-2 rounded-lg text-base font-medium hover:bg-slate-100 dark:hover:bg-slate-800">
          {{ link.label }}
        </a>
      </div>
    </header>

    <!-- Hero Section -->
    <section id="hero" class="min-h-screen flex items-center justify-center pt-24 pb-16 px-4 sm:px-6 lg:px-8 relative overflow-hidden">
      <div class="absolute top-1/4 left-1/2 -translate-x-1/2 w-96 h-96 bg-emerald-500/10 dark:bg-emerald-500/5 rounded-full blur-3xl pointer-events-none"></div>
      <div class="absolute bottom-1/4 right-10 w-80 h-80 bg-cyan-500/10 dark:bg-cyan-500/5 rounded-full blur-3xl pointer-events-none"></div>

      <div class="max-w-4xl mx-auto text-center relative z-10">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 text-xs font-semibold mb-6 tracking-wide uppercase border border-emerald-500/20">
          <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
          Vue 3 & TypeScript Developer
        </div>
        
        <h1 class="text-4xl sm:text-6xl lg:text-7xl font-extrabold tracking-tight mb-6">
          Hi, I'm <span class="bg-gradient-to-r from-emerald-500 via-teal-400 to-cyan-500 bg-clip-text text-transparent">{{ profile.name }}</span>
        </h1>
        
        <p class="text-lg sm:text-xl text-slate-600 dark:text-slate-400 max-w-2xl mx-auto mb-10 leading-relaxed">
          {{ profile.bio }}
        </p>

        <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
          <a href="#projects" class="w-full sm:w-auto px-8 py-3.5 rounded-xl bg-emerald-500 hover:bg-emerald-600 text-white font-semibold shadow-lg shadow-emerald-500/25 transition-all transform hover:-translate-y-0.5">
            Explore Projects
          </a>
          <a href="#contact" class="w-full sm:w-auto px-8 py-3.5 rounded-xl bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 dark:hover:bg-slate-700 font-semibold transition-all">
            Get in Touch
          </a>
        </div>

        <div class="mt-16 pt-8 border-t border-slate-200 dark:border-slate-800/80 flex flex-wrap justify-center items-center gap-6 text-sm text-slate-500 font-mono">
          <span class="flex items-center gap-1.5"><span class="w-2 h-2 rounded-full bg-emerald-500"></span> Vue 3 Composition API</span>
          <span class="flex items-center gap-1.5"><span class="w-2 h-2 rounded-full bg-blue-500"></span> TypeScript</span>
          <span class="flex items-center gap-1.5"><span class="w-2 h-2 rounded-full bg-cyan-500"></span> Tailwind CSS</span>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 bg-slate-100/50 dark:bg-slate-900/50 border-y border-slate-200 dark:border-slate-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <h2 class="text-3xl sm:text-4xl font-bold tracking-tight mb-4">About Me</h2>
          <p class="text-slate-600 dark:text-slate-400">Passionate about building scalable web applications with clean, typed code and modern interfaces.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="(item, index) in aboutCards" :key="index" class="p-8 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 shadow-sm hover:shadow-md transition-shadow">
            <div class="w-12 h-12 rounded-xl bg-emerald-500/10 text-emerald-500 flex items-center justify-center font-bold text-lg mb-6">
              0{{ index + 1 }}
            </div>
            <h3 class="text-xl font-semibold mb-3">{{ item.title }}</h3>
            <p class="text-slate-600 dark:text-slate-400 text-sm leading-relaxed">{{ item.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-24 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center max-w-3xl mx-auto mb-16">
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight mb-4">Technical Skills</h2>
        <p class="text-slate-600 dark:text-slate-400">Technologies and tools I use to bring ideas to life.</p>
      </div>

      <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-4 gap-4">
        <div v-for="skill in skills" :key="skill.name" class="p-5 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 flex items-center gap-4 hover:border-emerald-500/50 transition-all group">
          <div class="w-10 h-10 rounded-xl bg-slate-100 dark:bg-slate-800 flex items-center justify-center text-xl group-hover:scale-110 transition-transform">
            {{ skill.icon }}
          </div>
          <div>
            <h4 class="font-semibold text-sm">{{ skill.name }}</h4>
            <span class="text-xs text-slate-500">{{ skill.level }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-24 bg-slate-100/50 dark:bg-slate-900/50 border-y border-slate-200 dark:border-slate-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <h2 class="text-3xl sm:text-4xl font-bold tracking-tight mb-4">Featured Projects</h2>
          <p class="text-slate-600 dark:text-slate-400">Here are some of my recent works built with Vue 3, TypeScript & Tailwind.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div v-for="project in projects" :key="project.id" class="rounded-2xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 overflow-hidden flex flex-col group hover:shadow-xl transition-all">
            <div class="h-48 overflow-hidden relative">
              <img :src="project.image" :alt="project.title" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
              <div class="absolute inset-0 bg-gradient-to-t from-slate-900/60 to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end p-4">
                <span class="text-xs font-medium text-white px-2.5 py-1 rounded-md bg-emerald-500/80 backdrop-blur-sm">{{ project.category }}</span>
              </div>
            </div>
            <div class="p-6 flex-1 flex flex-col justify-between">
              <div>
                <h3 class="text-xl font-bold mb-2 group-hover:text-emerald-500 transition-colors">{{ project.title }}</h3>
                <p class="text-slate-600 dark:text-slate-400 text-sm mb-4 leading-relaxed">{{ project.description }}</p>
              </div>
              <div>
                <div class="flex flex-wrap gap-2 mb-6">
                  <span v-for="tech in project.techStack" :key="tech" class="px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-xs font-mono text-emerald-600 dark:text-emerald-400">
                    {{ tech }}
                  </span>
                </div>
                <div class="flex items-center gap-4 pt-4 border-t border-slate-100 dark:border-slate-800">
                  <a :href="project.github" target="_blank" class="text-sm font-semibold hover:text-emerald-500 flex items-center gap-1.5">
                    GitHub Code
                  </a>
                  <a :href="project.liveDemo" target="_blank" class="text-sm font-semibold text-emerald-500 hover:underline flex items-center gap-1.5">
                    Live Preview
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center max-w-2xl mx-auto mb-16">
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight mb-4">Get In Touch</h2>
        <p class="text-slate-600 dark:text-slate-400">Have a project in mind or want to collaborate? Feel free to drop a message.</p>
      </div>

      <div class="rounded-2xl bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 p-8 sm:p-12 shadow-sm">
        <form @submit.prevent="handleSubmit" class="space-y-6">
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
            <div>
              <label class="block text-sm font-medium mb-2">Your Name</label>
              <input v-model="form.name" type="text" required class="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 focus:outline-none focus:border-emerald-500 transition-colors" placeholder="John Doe" />
            </div>
            <div>
              <label class="block text-sm font-medium mb-2">Your Email</label>
              <input v-model="form.email" type="email" required class="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 focus:outline-none focus:border-emerald-500 transition-colors" placeholder="john@example.com" />
            </div>
          </div>
          <div>
            <label class="block text-sm font-medium mb-2">Subject</label>
            <input v-model="form.subject" type="text" required class="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 focus:outline-none focus:border-emerald-500 transition-colors" placeholder="Project Inquiry" />
          </div>
          <div>
            <label class="block text-sm font-medium mb-2">Message</label>
            <textarea v-model="form.message" rows="5" required class="w-full px-4 py-3 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 focus:outline-none focus:border-emerald-500 transition-colors" placeholder="Tell me about your project..."></textarea>
          </div>
          
          <button type="submit" class="w-full py-4 rounded-xl bg-emerald-500 hover:bg-emerald-600 text-white font-semibold shadow-lg shadow-emerald-500/25 transition-all">
            Send Message
          </button>

          <div v-if="submitted" class="p-4 rounded-xl bg-emerald-500/10 border border-emerald-500/20 text-emerald-600 dark:text-emerald-400 text-center text-sm font-medium">
            Thank you! Your message has been successfully sent.
          </div>
        </form>
      </div>
    </section>

    <!-- Footer -->
    <footer class="py-12 border-t border-slate-200 dark:border-slate-800 bg-slate-100/30 dark:bg-slate-900/30">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4">
        <p class="text-sm text-slate-500">© 2026 {{ profile.name }}. Built with Vue 3, TypeScript & Tailwind CSS.</p>
        <div class="flex items-center space-x-6 text-sm text-slate-500">
          <a href="https://github.com/nikkoo11" target="_blank" class="hover:text-emerald-500 transition-colors">GitHub</a>
          <a href="#hero" class="hover:text-emerald-500 transition-colors">Back to Top ↑</a>
        </div>
      </div>
    </footer>
  </div>
</template>