<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const mobileMenuOpen = ref(false)
const features = [
  {
    icon: '🤖',
    title: 'AI-Powered Learning',
    description: 'Personalized learning paths adapted to your pace and style'
  },
  {
    icon: '📱',
    title: 'Mobile First',
    description: 'Learn anywhere, anytime with our mobile-optimized platform'
  },
  {
    icon: '🎯',
    title: 'Smart Progress Tracking',
    description: 'AI monitors your progress and suggests improvements'
  },
  {
    icon: '👥',
    title: 'Collaborative Learning',
    description: 'Connect with peers and learn together'
  },
  {
    icon: '📊',
    title: 'Real-time Analytics',
    description: 'Track your performance with detailed insights'
  },
  {
    icon: '🏆',
    title: 'Gamified Experience',
    description: 'Earn rewards and achievements as you learn'
  }
]

const goToAuth = () => {
  router.push('/auth')
}
</script>

<template>
  <div class="min-h-screen bg-base-100">
    <!-- Mobile-first Navigation -->
    <div class="navbar bg-base-100 shadow-lg sticky top-0 z-50">
      <div class="navbar-start">
        <div class="dropdown">
          <label tabindex="0" class="btn btn-ghost lg:hidden" @click="mobileMenuOpen = !mobileMenuOpen">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" />
            </svg>
          </label>
          <ul v-if="mobileMenuOpen" tabindex="0" class="menu menu-sm dropdown-content mt-3 z-[1] p-2 shadow bg-base-100 rounded-box w-52">
            <li><a href="#features">Features</a></li>
            <li><a href="#how-it-works">How it Works</a></li>
            <li><a href="#pricing">Pricing</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
        <a class="btn btn-ghost text-xl">Skooledin</a>
      </div>
      <div class="navbar-center hidden lg:flex">
        <ul class="menu menu-horizontal px-1">
          <li><a href="#features">Features</a></li>
          <li><a href="#how-it-works">How it Works</a></li>
          <li><a href="#pricing">Pricing</a></li>
          <li><a href="#contact">Contact</a></li>
        </ul>
      </div>
      <div class="navbar-end">
        <a @click="goToAuth" class="btn btn-primary btn-sm">Get Started</a>
      </div>
    </div>

    <!-- Hero Section -->
    <section class="hero min-h-[90vh] bg-gradient-to-br from-primary/10 to-secondary/10">
      <div class="hero-content text-center">
        <div class="max-w-md">
          <h1 class="text-4xl lg:text-5xl font-bold bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent">
            Learn Smarter with AI
          </h1>
          <p class="py-6 text-base-content/80">
            Skooledin revolutionizes education with personalized AI-powered learning experiences designed for the mobile generation.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button @click="goToAuth" class="btn btn-primary">Start Learning Free</button>
            <button class="btn btn-outline">Watch Demo</button>
          </div>
          <div class="mt-8">
            <img src="https://placehold.co/300x500/9333ea/ffffff?text=App+Preview" alt="App Preview" class="mx-auto rounded-2xl shadow-2xl" />
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section id="features" class="py-16 px-4">
      <div class="max-w-6xl mx-auto">
        <h2 class="text-3xl lg:text-4xl font-bold text-center mb-12">
          Features that Transform Learning
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="feature in features" :key="feature.title" class="card bg-base-200 shadow-xl hover:shadow-2xl transition-shadow">
            <div class="card-body">
              <div class="text-4xl mb-4">{{ feature.icon }}</div>
              <h3 class="card-title">{{ feature.title }}</h3>
              <p class="text-base-content/70">{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- How It Works Section -->
    <section id="how-it-works" class="py-16 px-4 bg-base-200">
      <div class="max-w-4xl mx-auto">
        <h2 class="text-3xl lg:text-4xl font-bold text-center mb-12">
          How Skooledin Works
        </h2>
        <div class="space-y-8">
          <div class="flex flex-col md:flex-row items-center gap-6">
            <div class="badge badge-primary badge-lg">1</div>
            <div class="flex-1">
              <h3 class="text-xl font-semibold mb-2">Sign Up & Set Goals</h3>
              <p class="text-base-content/70">Create your profile and tell us what you want to learn</p>
            </div>
          </div>
          <div class="flex flex-col md:flex-row items-center gap-6">
            <div class="badge badge-primary badge-lg">2</div>
            <div class="flex-1">
              <h3 class="text-xl font-semibold mb-2">AI Creates Your Path</h3>
              <p class="text-base-content/70">Our AI analyzes your goals and creates a personalized learning journey</p>
            </div>
          </div>
          <div class="flex flex-col md:flex-row items-center gap-6">
            <div class="badge badge-primary badge-lg">3</div>
            <div class="flex-1">
              <h3 class="text-xl font-semibold mb-2">Learn & Grow</h3>
              <p class="text-base-content/70">Study at your own pace with AI-powered assistance and real-time feedback</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section class="py-16 px-4">
      <div class="max-w-4xl mx-auto text-center">
        <h2 class="text-3xl lg:text-4xl font-bold mb-6">
          Ready to Transform Your Learning?
        </h2>
        <p class="text-lg mb-8 text-base-content/70">
          Join thousands of students already learning smarter with Skooledin
        </p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button @click="goToAuth" class="btn btn-primary btn-lg">Get Started Now</button>
          <button class="btn btn-outline btn-lg">Schedule Demo</button>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer p-10 bg-base-200 text-base-content">
      <div>
        <span class="footer-title">Skooledin</span>
        <p class="max-w-xs">AI-powered education platform making learning accessible and personalized for everyone.</p>
      </div>
      <div>
        <span class="footer-title">Product</span>
        <a class="link link-hover">Features</a>
        <a class="link link-hover">Pricing</a>
        <a class="link link-hover">API</a>
        <a class="link link-hover">Integrations</a>
      </div>
      <div>
        <span class="footer-title">Company</span>
        <a class="link link-hover">About</a>
        <a class="link link-hover">Blog</a>
        <a class="link link-hover">Careers</a>
        <a class="link link-hover">Contact</a>
      </div>
      <div>
        <span class="footer-title">Legal</span>
        <a class="link link-hover">Terms of Service</a>
        <a class="link link-hover">Privacy Policy</a>
        <a class="link link-hover">Cookie Policy</a>
      </div>
    </footer>
  </div>
</template>

<style scoped>
</style>