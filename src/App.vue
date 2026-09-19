<script setup lang="ts">
import { ref } from 'vue'

const developer = ref({
  name: 'Jericho Fragata',
  title: '4th Year Computer Engineering Student & Developer',
  bio: 'Specializing as a 4th Year Computer Engineering Student, focusing on building high-performance web applications and hardware-software concepts using Vue 3, TypeScript, and Tailwind CSS.',
  github: 'https://github.com/nikkoo11/portfolio',
  email: 'contact@jericho.dev',
  skills: [
    { name: 'Vue 3 & Composition API', level: 'Advanced' },
    { name: 'TypeScript', level: 'Intermediate' },
    { name: 'Tailwind CSS', level: 'Advanced' },
    { name: 'Computer Engineering', level: 'Specialization' },
    { name: 'Vite & Build Tools', level: 'Intermediate' },
    { name: 'Git & GitHub', level: 'Intermediate' }
  ],
  projects: [
    {
      title: 'Portfolio Website',
      description: 'A responsive, interactive developer portfolio built strictly with Vue 3, TypeScript, and Tailwind CSS.',
      tech: ['Vue 3', 'TypeScript', 'Tailwind CSS'],
      link: 'https://github.com/nikkoo11/portfolio'
    },
    {
      title: 'Cinematic Beach & Style Concepts',
      description: 'A creative prompt engineering project designing moody night photography and digital aesthetic transformations.',
      tech: ['Prompt Engineering', 'Visual Design'],
      link: '#'
    }
  ]
})

const emailCopied = ref(false)
const copyEmail = () => {
  navigator.clipboard.writeText(developer.value.email)
  emailCopied.value = true
  setTimeout(() => { emailCopied.value = false }, 2000)
}
</script>

<template>
  <div class="min-h-screen bg-slate-950 text-slate-100 font-sans selection:bg-purple-500 selection:text-white relative overflow-hidden">
    
    <!-- Ambient Background Glow Effects -->
    <div class="absolute top-0 left-1/4 w-[500px] h-[500px] bg-purple-600/10 rounded-full blur-[120px] pointer-events-none"></div>
    <div class="absolute top-1/2 right-10 w-[400px] h-[400px] bg-pink-600/10 rounded-full blur-[120px] pointer-events-none"></div>

    <!-- Sticky Navigation Bar -->
    <header class="sticky top-0 z-50 backdrop-blur-xl bg-slate-950/80 border-b border-slate-800/80">
      <div class="max-w-5xl mx-auto px-6 h-16 flex justify-between items-center">
        <a href="#home" class="font-mono text-xs text-purple-400 font-semibold tracking-wider flex items-center gap-2">
          <span class="w-2 h-2 rounded-full bg-purple-500 animate-pulse"></span>
          // JERICHO.FRAGATA
        </a>
        <nav class="hidden sm:flex gap-6 text-xs font-mono font-medium text-slate-300">
          <a href="#home" class="hover:text-purple-400 transition">Home</a>
          <a href="#skills" class="hover:text-purple-400 transition">Skills</a>
          <a href="#projects" class="hover:text-purple-400 transition">Projects</a>
          <a href="#contact" class="hover:text-purple-400 transition">Contact</a>
        </nav>
      </div>
    </header>

    <!-- Main Content Container -->
    <main class="max-w-5xl mx-auto px-6 space-y-28 py-16">

      <!-- HOME SECTION -->
      <section id="home" class="min-h-[80vh] flex flex-col justify-center space-y-8 pt-10">
        <div class="space-y-4 max-w-2xl">
          <span class="text-xs font-mono font-semibold px-3 py-1 rounded-full bg-purple-950/80 text-purple-300 border border-purple-800/80 tracking-wider inline-block">
            PORTFOLIO.TS
          </span>
          <h1 class="text-5xl md:text-7xl font-bold tracking-tight text-white">
            Hi, I'm <span class="bg-gradient-to-r from-purple-400 via-pink-400 to-purple-500 bg-clip-text text-transparent">{{ developer.name }}</span>
          </h1>
          <p class="text-purple-400 font-mono text-base md:text-lg font-semibold">
            {{ developer.title }}
          </p>
        </div>

        <p class="text-slate-300 text-base md:text-lg leading-relaxed max-w-xl">
          Specializing as a <strong class="text-white font-semibold">4th Year Computer Engineering Student</strong>, focusing on building high-performance web applications with <strong class="text-purple-300 font-semibold">Vue 3</strong>, <strong class="text-purple-300 font-semibold">TypeScript</strong>, and <strong class="text-purple-300 font-semibold">Tailwind CSS</strong>.
        </p>

        <div class="flex gap-4 pt-2">
          <a href="#projects" class="px-6 py-3 rounded-xl bg-gradient-to-r from-purple-600 to-pink-600 hover:opacity-90 text-white text-sm font-semibold transition shadow-lg shadow-purple-600/25">
            Explore Projects
          </a>
          <a href="#contact" class="px-6 py-3 rounded-xl bg-slate-900 hover:bg-slate-800 border border-slate-800 text-slate-300 text-sm font-semibold transition">
            Get in Touch
          </a>
        </div>
      </section>

      <!-- SKILLS SECTION -->
      <section id="skills" class="space-y-8 pt-10">
        <div>
          <span class="text-xs font-mono text-purple-400 uppercase tracking-widest font-semibold">// EXPERTISE</span>
          <h2 class="text-3xl font-bold tracking-tight text-white mt-1">Technical Skills</h2>
          <p class="text-slate-400 text-sm mt-1">Core competencies and academic toolkit.</p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
          <div v-for="skill in developer.skills" :key="skill.name" class="p-5 rounded-2xl bg-slate-900/80 border border-slate-800/80 backdrop-blur-md flex justify-between items-center transition hover:border-purple-500/40 hover:bg-slate-900">
            <span class="text-slate-200 font-mono text-sm font-medium">{{ skill.name }}</span>
            <span class="text-xs px-2.5 py-1 rounded-md bg-purple-950/80 border border-purple-900 text-purple-300 font-mono">
              {{ skill.level }}
            </span>
          </div>
        </div>
      </section>

      <!-- PROJECTS SECTION -->
      <section id="projects" class="space-y-8 pt-10">
        <div>
          <span class="text-xs font-mono text-purple-400 uppercase tracking-widest font-semibold">// PORTFOLIO</span>
          <h2 class="text-3xl font-bold tracking-tight text-white mt-1">Featured Projects</h2>
          <p class="text-slate-400 text-sm mt-1">Explore my development work and repositories.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div v-for="project in developer.projects" :key="project.title" class="p-6 rounded-2xl bg-slate-900/80 border border-slate-800/80 backdrop-blur-md space-y-5 flex flex-col justify-between hover:border-purple-500/50 transition group">
            <div class="space-y-3">
              <h3 class="text-xl font-bold text-white group-hover:text-purple-300 transition">{{ project.title }}</h3>
              <p class="text-slate-400 text-sm leading-relaxed">{{ project.description }}</p>
            </div>
            <div class="space-y-4 pt-2">
              <div class="flex flex-wrap gap-1.5">
                <span v-for="t in project.tech" :key="t" class="text-xs px-2.5 py-1 rounded-md bg-slate-800/80 border border-slate-700 text-purple-300 font-mono">
                  {{ t }}
                </span>
              </div>
              <a :href="project.link" target="_blank" class="inline-block text-xs font-mono font-semibold text-purple-400 hover:text-purple-300">
                View Repository &rarr;
              </a>
            </div>
          </div>
        </div>
      </section>

      <!-- CONTACT SECTION -->
      <section id="contact" class="space-y-8 pt-10 max-w-xl">
        <div>
          <span class="text-xs font-mono text-purple-400 uppercase tracking-widest font-semibold">// CONNECT</span>
          <h2 class="text-3xl font-bold tracking-tight text-white mt-1">Get In Touch</h2>
          <p class="text-slate-400 text-sm mt-1">Feel free to reach out for collaboration or inquiries.</p>
        </div>

        <div class="p-6 rounded-2xl bg-slate-900/80 border border-slate-800/80 backdrop-blur-md space-y-6">
          <div class="flex flex-col space-y-1">
            <span class="text-xs font-mono text-slate-400 uppercase tracking-wider">GitHub Repository</span>
            <a :href="developer.github" target="_blank" class="text-purple-400 font-mono text-sm hover:underline">
              {{ developer.github }}
            </a>
          </div>

          <div class="flex flex-col space-y-1 pt-2">
            <span class="text-xs font-mono text-slate-400 uppercase tracking-wider">Direct Email</span>
            <div class="flex items-center gap-3">
              <span class="text-slate-200 font-mono text-sm">{{ developer.email }}</span>
              <button @click="copyEmail" class="px-3.5 py-1.5 bg-gradient-to-r from-purple-600 to-pink-600 hover:opacity-90 text-white text-xs font-mono rounded-lg transition shadow-md shadow-purple-600/20">
                {{ emailCopied ? 'Copied!' : 'Copy Email' }}
              </button>
            </div>
          </div>
        </div>
      </section>

    </main>

    <!-- Footer -->
    <footer class="max-w-5xl mx-auto px-6 text-center py-12 border-t border-slate-800/80 text-xs font-mono text-slate-500">
      <p>© 2026 Jericho Fragata. Built with Vue 3, TypeScript, and Tailwind CSS.</p>
    </footer>

  </div>
</template>