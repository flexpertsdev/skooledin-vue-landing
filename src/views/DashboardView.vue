<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const navigateTo = (route) => {
  router.push(route)
}

const tabs = [
  { id: 'feed', route: '/feed', icon: '🏠', label: 'Feed' },
  { id: 'chat', route: '/chat', icon: '💬', label: 'Chat' },
  { id: 'notebook', route: '/notebook', icon: '📝', label: 'Notebook' }
]

const goToSettings = () => {
  router.push('/settings')
}
</script>

<template>
  <div class="min-h-screen bg-base-100">
    <!-- Top App Bar -->
    <div class="navbar bg-base-100 shadow-sm border-b border-base-300">
      <div class="navbar-start">
        <a class="btn btn-ghost text-xl">Skooledin</a>
      </div>
      <div class="navbar-end">
        <button @click="goToSettings" class="btn btn-ghost btn-circle">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
          </svg>
        </button>
      </div>
    </div>

    <!-- Dashboard Content -->
    <div class="flex flex-col items-center justify-center p-8">
      <h1 class="text-3xl font-bold mb-8">Welcome to Skooledin</h1>
      <p class="text-base-content/70 mb-12 text-center max-w-md">
        Choose where you'd like to go:
      </p>
      
      <!-- Navigation Cards -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6 w-full max-w-4xl">
        <div 
          v-for="tab in tabs" 
          :key="tab.id"
          @click="navigateTo(tab.route)"
          class="card bg-base-200 shadow-xl hover:shadow-2xl transition-all cursor-pointer hover:scale-105"
        >
          <div class="card-body items-center text-center">
            <div class="text-6xl mb-4">{{ tab.icon }}</div>
            <h2 class="card-title">{{ tab.label }}</h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>