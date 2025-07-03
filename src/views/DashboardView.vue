<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import Feed from '../components/Feed.vue'
import Chat from '../components/Chat.vue'
import Notebook from '../components/Notebook.vue'

const router = useRouter()
const activeTab = ref('feed')

const tabs = [
  { id: 'feed', icon: '🏠', component: Feed },
  { id: 'chat', icon: '💬', component: Chat },
  { id: 'notebook', icon: '📝', component: Notebook }
]

const currentComponent = ref(Feed)

const switchTab = (tabId) => {
  activeTab.value = tabId
  const tab = tabs.find(t => t.id === tabId)
  currentComponent.value = tab.component
}

const goToSettings = () => {
  router.push('/settings')
}
</script>

<template>
  <div class="h-screen flex flex-col bg-base-100">
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

    <!-- Main Content Area -->
    <div class="flex-1 overflow-y-auto pb-16">
      <component :is="currentComponent" />
    </div>

    <!-- Bottom Dock Navigation -->
    <div class="btm-nav btm-nav-md bg-base-200 border-t border-base-300">
      <button 
        v-for="tab in tabs" 
        :key="tab.id"
        @click="switchTab(tab.id)"
        :class="['transition-all', activeTab === tab.id ? 'active' : '']"
      >
        <span class="text-2xl">{{ tab.icon }}</span>
      </button>
    </div>
  </div>
</template>

<style scoped>
.btm-nav button {
  @apply flex items-center justify-center;
}

.btm-nav button.active {
  @apply bg-primary text-primary-content;
}

.btm-nav button:not(.active) {
  @apply hover:bg-base-300;
}
</style>