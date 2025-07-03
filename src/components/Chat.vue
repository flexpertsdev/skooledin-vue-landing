<script setup>
import { ref } from 'vue'

const messages = ref([
  {
    id: 1,
    sender: 'AI Assistant',
    avatar: '🤖',
    content: 'Hello! How can I help you with your studies today?',
    time: '10:30 AM',
    isAI: true
  },
  {
    id: 2,
    sender: 'You',
    content: 'I need help understanding calculus derivatives',
    time: '10:32 AM',
    isAI: false
  },
  {
    id: 3,
    sender: 'AI Assistant',
    avatar: '🤖',
    content: 'I\'d be happy to help you understand derivatives! Let\'s start with the basics. A derivative represents the rate of change of a function at any given point.',
    time: '10:33 AM',
    isAI: true
  }
])

const newMessage = ref('')

const sendMessage = () => {
  if (newMessage.value.trim()) {
    messages.value.push({
      id: messages.value.length + 1,
      sender: 'You',
      content: newMessage.value,
      time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }),
      isAI: false
    })
    newMessage.value = ''
    
    // Simulate AI response
    setTimeout(() => {
      messages.value.push({
        id: messages.value.length + 1,
        sender: 'AI Assistant',
        avatar: '🤖',
        content: 'I understand your question. Let me help you with that...',
        time: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }),
        isAI: true
      })
    }, 1000)
  }
}
</script>

<template>
  <div class="flex flex-col h-full">
    <!-- Chat Header -->
    <div class="p-4 border-b border-base-300">
      <h2 class="text-xl font-bold flex items-center gap-2">
        <span class="text-2xl">🤖</span>
        AI Study Assistant
      </h2>
    </div>
    
    <!-- Messages Area -->
    <div class="flex-1 overflow-y-auto p-4 space-y-4">
      <div 
        v-for="message in messages" 
        :key="message.id"
        :class="['chat', message.isAI ? 'chat-start' : 'chat-end']"
      >
        <div v-if="message.isAI" class="chat-image avatar">
          <div class="w-10 rounded-full">
            <div class="text-2xl flex items-center justify-center h-10">{{ message.avatar }}</div>
          </div>
        </div>
        <div class="chat-header">
          {{ message.sender }}
          <time class="text-xs opacity-50 ml-1">{{ message.time }}</time>
        </div>
        <div :class="['chat-bubble', message.isAI ? 'chat-bubble-primary' : '']">
          {{ message.content }}
        </div>
      </div>
    </div>
    
    <!-- Input Area -->
    <div class="p-4 border-t border-base-300">
      <form @submit.prevent="sendMessage" class="flex gap-2">
        <input 
          v-model="newMessage"
          type="text" 
          placeholder="Type your message..." 
          class="input input-bordered flex-1"
        />
        <button type="submit" class="btn btn-primary">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
          </svg>
        </button>
      </form>
    </div>
  </div>
</template>