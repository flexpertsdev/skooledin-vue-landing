<script setup>
const posts = [
  {
    id: 1,
    author: 'AI Tutor',
    avatar: '🤖',
    time: '2 hours ago',
    content: 'Great progress on your Math course! You\'ve completed 75% of the Algebra module. Keep it up! 🎉',
    likes: 12,
    comments: 3
  },
  {
    id: 2,
    author: 'Study Group',
    avatar: '👥',
    time: '4 hours ago',
    content: 'New study session scheduled for Physics tomorrow at 3 PM. Who\'s joining?',
    likes: 8,
    comments: 5
  },
  {
    id: 3,
    author: 'Course Update',
    avatar: '📚',
    time: '1 day ago',
    content: 'New content added to the Python Programming course! Check out the advanced data structures module.',
    likes: 24,
    comments: 7
  }
]
</script>

<template>
  <div class="p-4 space-y-4 max-w-2xl mx-auto">
    <h2 class="text-2xl font-bold mb-4">Your Feed</h2>
    
    <!-- Post Card -->
    <div v-for="post in posts" :key="post.id" class="card bg-base-200 shadow-md">
      <div class="card-body">
        <div class="flex items-start space-x-3">
          <div class="text-3xl">{{ post.avatar }}</div>
          <div class="flex-1">
            <div class="flex items-center justify-between">
              <h3 class="font-semibold">{{ post.author }}</h3>
              <span class="text-sm text-base-content/60">{{ post.time }}</span>
            </div>
            <p class="mt-2 text-base-content/80">{{ post.content }}</p>
            
            <!-- Actions -->
            <div class="flex items-center gap-4 mt-4">
              <button class="btn btn-ghost btn-sm gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
                </svg>
                {{ post.likes }}
              </button>
              <button class="btn btn-ghost btn-sm gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z" />
                </svg>
                {{ post.comments }}
              </button>
              <button class="btn btn-ghost btn-sm">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m9.632 4.684C18.114 16.062 18 16.518 18 17c0 .482.114.938.316 1.342m0-2.684a3 3 0 110 2.684M9.316 8.658C9.114 9.062 9 9.518 9 10c0 .482.114.938.316 1.342M9.316 8.658a3 3 0 110 2.684m9.368 4.316a3 3 0 110 2.684" />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>